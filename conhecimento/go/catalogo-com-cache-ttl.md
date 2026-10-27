---
tipo: conceito
criado_em: 2026-10-27
atualizado_em: 2026-10-27
tags: [go, cache, ttl, concorrencia]
---

# Catálogo com cache TTL em Go

## Resumo

O exemplo mantém um catálogo de metadados em memória e o reutiliza por um minuto desde a última carga bem-sucedida. Depois do prazo, a próxima chamada tenta buscar uma nova versão no banco. Se a busca falhar, usa a última versão disponível, quando existe. O cache guarda as definições dos campos e fatores, não os resultados das buscas de funcionários.

## Como funciona

Pense no catálogo como uma ficha de consulta que fica na mesa. O TTL indica quando conferir se ela mudou; ele não manda alguém atualizá-la sozinho.

1. `NewCatalog` cria o cache compartilhado no processo. `main.go` configura `time.Minute`.
2. `Get` adquire o mutex e devolve o snapshot se ele ainda estiver dentro do TTL.
3. Quando falta uma versão ou o prazo venceu, `loadSnapshot` consulta `attribute_definitions` e `risk_factors` e monta listas e mapas de acesso por chave.
4. Somente uma carga bem-sucedida substitui o snapshot e atualiza `loadedAt`.
5. `Invalidate` zera `loadedAt`. A consulta ocorre no próximo `Get`, inclusive quando a invalidação veio de `POST /internal/catalog/reload`.

Após receber o ponteiro, o consumidor lê o snapshot sem manter o lock do catálogo. A versão antiga pode continuar referenciada por uma requisição enquanto outra usa a nova.

## O trecho que explica a decisão

Trecho real de `Catalog.Get`, analisado estaticamente:

```go
snap, err := loadSnapshot(ctx, c.db)
if err != nil {
    if c.snap != nil {
        return c.snap, nil // usa a última versão disponível
    }
    return nil, err
}
c.snap, c.loadedAt = snap, time.Now()
return snap, nil
```

O comentário acima foi abreviado para estudo; o comportamento foi preservado. O fallback favorece continuidade de leitura, aceitando metadados antigos. Sem uma primeira carga válida, o erro chega ao chamador.

## Decisões para levar a outro projeto

- **Frescor:** decidir se metadados antigos são aceitáveis e por quanto tempo. Neste código, o fallback não tem limite próprio de idade.
- **Concorrência:** o mutex permanece adquirido durante a consulta ao banco. Isso evita recargas simultâneas por catálogo, mas os demais `Get` aguardam a recarga.
- **Falhas repetidas:** uma recarga que falhou não renova `loadedAt`; novas chamadas podem tentar novamente, sem espera progressiva implementada.
- **Somente leitura:** a imutabilidade é uma convenção. Os slices exportados e recebidos pelo construtor podem ser modificados; Go não impede essas alterações automaticamente.
- **Várias instâncias:** cada processo tem seu cache e sua invalidação. O exemplo não sincroniza réplicas.

O padrão é adequado quando um catálogo pequeno é muito consultado e sua atualização não precisa aparecer instantaneamente. Esses critérios precisam ser conferidos na aplicação de destino.

## Perguntas para revisar

1. O que acontece se passar um minuto sem nenhuma requisição?
2. Por que zerar `loadedAt` é diferente de buscar o catálogo imediatamente?
3. Se o banco ficar indisponível por horas, qual versão será usada? Isso atende ao seu caso?
4. Que contrato os consumidores precisam respeitar para compartilhar o snapshot com segurança?

## Fontes e relações

Verificação em 2026-10-27, revisão `dca8e1e9cfd892dc0239e24f42a2113a6b8bb592`:

- [Catálogo, snapshot, mutex e invalidação](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/internal/analytics/catalog.go).
- [Configuração do TTL](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/cmd/api/main.go).
- [Handler de invalidação](https://github.com/j-ordep/go-in-memory-ttl-cache-example/blob/dca8e1e9cfd892dc0239e24f42a2113a6b8bb592/internal/httpapi/server.go).
- [Experiência de extrair um caso genérico](../../experiencias/2026-10-27-case-generico-cache-go.md).
- [Filtros orientados pelo catálogo](../banco-de-dados/filtros-dinamicos-parametrizados.md).

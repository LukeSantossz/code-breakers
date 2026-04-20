# 49 - Group Anagrams

## Informações

| Campo | Valor |
|-------|-------|
| **Link** | [LeetCode](https://leetcode.com/problems/group-anagrams/) |
| **Dificuldade** | Medium |
| **Tópicos** | Array, Hash Table, String, Sorting |

## Enunciado

Dado um array de strings `strs`, agrupe os anagramas juntos. Você pode retornar a resposta em qualquer ordem.

**Exemplo:**
```
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

## Abordagem

Usar a versão ordenada de cada string como chave do Hash Map:

1. Criar um defaultdict de listas
2. Para cada string, ordenar seus caracteres para criar uma chave
3. Adicionar a string original ao grupo correspondente
4. Retornar todos os grupos

## Complexidade

| Tipo | Complexidade |
|------|--------------|
| **Tempo** | O(n * k log k) onde n = número de strings, k = tamanho máximo da string |
| **Espaço** | O(n * k) |

## Solução

```python
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs: list[str]) -> list[list[str]]:
        groups = defaultdict(list)

        for s in strs:
            key = tuple(sorted(s))
            groups[key].append(s)

        return list(groups.values())
```

## Notas e Aprendizados

- Anagramas têm a mesma representação quando ordenados
- defaultdict evita verificar se a chave existe
- Alternativa: usar contagem de caracteres como chave (evita sorting)
- Versão com contagem: `key = tuple([s.count(c) for c in 'abcdefghijklmnopqrstuvwxyz'])`

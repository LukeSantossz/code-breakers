# 242 - Valid Anagram

## Informações

| Campo | Valor |
|-------|-------|
| **Link** | [LeetCode](https://leetcode.com/problems/valid-anagram/) |
| **Dificuldade** | Easy |
| **Tópicos** | Hash Table, String, Sorting |

## Enunciado

Dadas duas strings `s` e `t`, retorne `true` se `t` é um anagrama de `s`, e `false` caso contrário.

**Exemplo:**
```
Input: s = "anagram", t = "nagaram"
Output: true
```

## Abordagem

Usar um Hash Map para contar a frequência de cada caractere:

1. Verificar se as strings têm o mesmo tamanho
2. Contar frequência de cada caractere em `s`
3. Decrementar contagem para cada caractere em `t`
4. Se algum caractere não existir ou contagem ficar negativa, retornar False

## Complexidade

| Tipo | Complexidade |
|------|--------------|
| **Tempo** | O(n) |
| **Espaço** | O(1) - no máximo 26 letras |

## Solução

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        count = {}
        for char in s:
            count[char] = count.get(char, 0) + 1

        for char in t:
            if char not in count:
                return False
            count[char] -= 1
            if count[char] < 0:
                return False

        return True
```

## Notas e Aprendizados

- Anagrama = mesmos caracteres com mesma frequência, ordem diferente
- Alternativa: ordenar ambas strings e comparar (O(n log n))
- Solução com Counter: `return Counter(s) == Counter(t)`

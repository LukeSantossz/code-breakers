# 217 - Contains Duplicate

## Informações

| Campo | Valor |
|-------|-------|
| **Link** | [LeetCode](https://leetcode.com/problems/contains-duplicate/) |
| **Dificuldade** | Easy |
| **Tópicos** | Arrays, Hash Table |

## Enunciado

Dado um array de inteiros `nums`, retorne `true` se algum valor aparecer pelo menos duas vezes no array, e `false` se todos os elementos forem distintos.

**Exemplo:**
```
Input: nums = [1,2,3,1]
Output: true
```

## Abordagem

Utilizar um Hash Set para rastrear os números já vistos:

1. Criar um set vazio
2. Iterar pelo array
3. Para cada número, verificar se já está no set
4. Se estiver, retornar True (duplicata encontrada)
5. Se não, adicionar ao set
6. Se terminar o loop, retornar False

## Complexidade

| Tipo | Complexidade |
|------|--------------|
| **Tempo** | O(n) |
| **Espaço** | O(n) |

## Solução

```python
class Solution:
    def containsDuplicate(self, nums: list[int]) -> bool:
        seen = set()
        for num in nums:
            if num in seen:
                return True
            seen.add(num)
        return False
```

## Notas e Aprendizados

- Hash Set permite verificação O(1) para existência de elemento
- Alternativa: ordenar o array e verificar adjacentes (O(n log n) tempo, O(1) espaço)
- Solução mais pythonica: `return len(nums) != len(set(nums))`

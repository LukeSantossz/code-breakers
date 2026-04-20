# 1 - Two Sum

## Informações

| Campo | Valor |
|-------|-------|
| **Link** | [LeetCode](https://leetcode.com/problems/two-sum/) |
| **Dificuldade** | Easy |
| **Tópicos** | Array, Hash Table |

## Enunciado

Dado um array de inteiros `nums` e um inteiro `target`, retorne os índices dos dois números que somam ao `target`.

Você pode assumir que cada input tem exatamente uma solução, e você não pode usar o mesmo elemento duas vezes.

**Exemplo:**
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explicação: nums[0] + nums[1] == 9, então retornamos [0, 1]
```

## Abordagem

Usar um Hash Map para armazenar valores já vistos e seus índices:

1. Criar um dicionário vazio
2. Para cada número, calcular o complemento (target - num)
3. Se o complemento existir no dicionário, encontramos o par
4. Caso contrário, armazenar o número atual e seu índice

## Complexidade

| Tipo | Complexidade |
|------|--------------|
| **Tempo** | O(n) |
| **Espaço** | O(n) |

## Solução

```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        seen = {}
        for i, num in enumerate(nums):
            complement = target - num
            if complement in seen:
                return [seen[complement], i]
            seen[num] = i
        return []
```

## Notas e Aprendizados

- Problema clássico #1 do LeetCode
- Hash Map transforma busca O(n) em O(1)
- Alternativa brute force: dois loops aninhados O(n²)
- Importante: retornar índices, não os valores

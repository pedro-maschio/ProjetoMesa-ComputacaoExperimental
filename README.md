# Projeto de Computação Experimental, por Pedro de Torres Maschio

## Instruções
Para o modelo funcionar, é preciso instalar o Mesa da versão disponível no github, fazendo uso do seguinte comando:

```
pip install -e git+https://github.com/projectmesa/mesa#egg=mesa
```

O modelo escolhido foi o [wolf_sheep](https://github.com/projectmesa/mesa/tree/main/examples/wolf_sheep) que é uma simulação sobre um sistema predador-presa. As características dessa simulação são:
- Há três tipos de agentes: lobos, ovelhas e grama;
- Os lobos e ovelhas perambulam pelo grid, ambos gastam energia ao andar. Lobos recarregam a energia ao comer ovelha, ovelhas recarregam a energia ao comer grama;
- Lobos comem as ovelhas se estiverem na mesma célula.

Minha hipótese para a modificação da simulação foi adicionar a característica de probabilidade de "doença" no agente de Presa (na ovelha), de tal modo que um predador não vai querer comê-la. Quanto maior a probabilidade de estar doente, maior a probabilidade de esta ovelha não ser comida por um lobo. O limite
de probabilidade que vai definir se a ovelha vai ser comida ou não poderá ser definido pelo usuário na interface da simulação.

As modificações e suas justificativas foram:
- No modelo, foi adicionado a variável `diseaseLimiar`, que define um limiar de doença permitido para um lobo comer a ovelha. O valor mínimo é de 0.01, os passos são de 0.01 e o valor máximo é 1. 
- Para cada ovelha foi adicionada a variável `diseaseProbability`, um valor real gerado aleatoriamente entre [0, 1), que define a probabilidade de esta determinada ovelha estar doente.
- No comportamento do agente lobo, ficou definido que ele só vai comer a ovelha se sua `diseaseProbability` for inferior ou igual ao `diseaseLimiar` definido pelo usuário.

O que eu esperei ver com a mudança: quanto menor o valor do `diseaseLimiar`, maior a probabilidade de que as ovelhas vão prevalecer, pois os lobos só vão querer comer as ovelhas com o `diseaseProbability` muito baixo. Por outro lado, quanto maior o valor do `diseaseLimiar`, mais próximo esta simulação vai estar da simulação original, pois a verificação no agente do lobo vai se tornar irrelevante.

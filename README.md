# Projeto de Computação Experimental, por Pedro de Torres Maschio

## Instruções
Para o modelo funcionar, é preciso instalar o Mesa da versão disponível no github, fazendo uso do seguinte comando:

```
pip install -e git+https://github.com/projectmesa/mesa#egg=mesa
```

Após a instalação, o modelo em modo gráfico pode ser executado com o comando:
```
mesa runserver
```
na raiz do diretório.

Para gerar as planilhas, foi utilizado a seguinte sequência de comandos:
```
python3
from wolf_sheep import model
model.roda()
```

## Descrição do modelo
O modelo escolhido foi o [wolf_sheep](https://github.com/projectmesa/mesa/tree/main/examples/wolf_sheep) que é uma simulação sobre um sistema predador-presa. As características dessa simulação são:
- Há três tipos de agentes: lobos, ovelhas e grama;
- Os lobos e ovelhas perambulam pelo grid, ambos gastam energia ao andar. Lobos recarregam a energia ao comer ovelhas, ovelhas recarregam a energia ao comer grama;
- Lobos comem as ovelhas se estiverem na mesma célula (essa característica será modificada no experimento).

## Descrição da hipótese e das modificações
Minha hipótese para a modificação da simulação foi adicionar a característica de probabilidade de "doença" no agente de Presa (na ovelha), e também um limiar de probabilidade na interface do usuário. Mesmo se estiver na mesma célula, um lobo só vai comer a ovelha se sua probabilidade de doença for superior ao limiar definido na interface do usuário. A justificativa dessa adição, foi a percepção de que lobos preferem presas doentes, pois estão mais lentas. As ovelhas que possuírem probabilidade de doença inferior ao limiar definido pelo usuário na interface não serão comidas. 


Minha modificação anterior tinha uma hipótese contrária a essa, mas após uma observação mais cuidadosa, percebi que na natureza, os animais preferem predar animais mais lentos e doentes, e não evitá-los.

As modificações e suas justificativas foram:
- No modelo, foi adicionado a variável `diseaseLimiar`, que define um limiar de doença permitido para um lobo comer a ovelha. O valor mínimo é de 0, os passos são de 0.01 e o valor máximo é 1. 
- Para cada ovelha foi adicionada a variável `diseaseProbability`, um valor real gerado aleatoriamente entre [0, 1), que define a probabilidade de esta determinada ovelha estar doente.
- No comportamento do agente lobo, ficou definido que ele só vai comer a ovelha se sua `diseaseProbability` for maior ou igual ao `diseaseLimiar` definido pelo usuário.



## Planilhas

Segue abaixo uma descrição de cada umas das colunas das planilhas:

- **RunId**: id da execução, número inteiro
- **iteration**: iteração atual.
- **Step**: passo atual.
- **width**: tamanho da grid.
- **height**: tamanho da grid.
- **sheep_reproduce**: probabilidade de casa ovelha reproduzir a cada passo.
- **wolf_reproduce**: probabilidade de cada lobo reproduzir a cada passo.
- **wolf_gain_from_food**: energia que os lobos ganham da grama.
- **grass**: se a grama está habilitada (inicialmente verdadeiro nas simulações).
- **grass_regrowth_time**:  quanto tempo a grama demora para crescer após ser comida.
- **sheep_gain_from_food**: energia que as ovelhas ganham da grama.
- **initial_sheep**: número de inicial de ovelhas.
- **initial_wolves**: número inicial de lobos.
- **diseaseLimiar**: limiar de doença, probabilidade.
- **Wolves**: número de lobos vivos.
- **Sheep**: número de ovelhas vivas.

## Experimentos

Os experimentos foram conduzidos definindo as variáveis de controle nos seguintes valores:

- `Grass Enabled`: Sim
- `Disease Limiar`: 0
- `Grass Regrowth Time`: 8
- `Initial Sheep Population`: 100
- `Sheep Reproduction Rate`: 0.2
- `Initial Wolf Population`: 50
- `Wolf Reproduction Rate`: 0.05
- `Wolf Gain From Food Rate`: 16
- `Sheep Gain From Food`: 4
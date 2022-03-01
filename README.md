# Projeto de Computação Experimental, por Pedro de Torres Maschio

## Instruções
Para o modelo funcionar, é preciso instalar o Mesa da versão disponível no github, fazendo uso do seguinte comando:

```
pip install -e git+https://github.com/projectmesa/mesa#egg=mesa
```

O modelo escolhido foi o [wolf_sheep](https://github.com/projectmesa/mesa/tree/main/examples/wolf_sheep), que é uma simulação sobre um sistema predador-presa. Tal sistema é denominado instável se uma espécie tende à extinção, e estável caso contrário.

Minha hipótese para a modificação da simulação foi adicionar a característica de probabilidade de "doença" mo agente de Presa, de tal modo que um predador não vai querer comê-la. Quanto maior a probabilidade de estar doente, maior a probabilidade de esta ovelha não ser presa de um lobo.

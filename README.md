<img width="2535" height="470" alt="CapaEDO" src="https://github.com/user-attachments/assets/2da7d92e-183d-4c36-b1e4-78909c77e9d5" />

<div align="center">
  
# Como a aplicação do método de Euler à descida do gradiente auxilia no treinamento de modelos de machine learning?
</div>

Projeto da disciplina de Equações Diferenciais, desenvolvido na Ilum Escola de Ciência (CNPEM).

## Sobre o projeto

Treinar um modelo de machine learning é um problema de otimização: é preciso ajustar parâmetros para minimizar uma função de erro. O algoritmo mais simples para isso é a descida do gradiente. Este projeto mostra que a descida do gradiente é o método de Euler aplicado a uma equação diferencial, o fluxo de gradiente, e usa essa conexão para entender como a otimização funciona na prática.

## A ideia central

Se imaginarmos que um parâmetro $\theta$ desce continuamente a ladeira da função de erro $L$, ele obedece à equação diferencial

$$\frac{d\theta}{dt} = -\nabla L(\theta).$$

O método de Euler resolve essa equação em passos de tamanho $h$, pela regra $\theta_{n+1} = \theta_n + h\, f(\theta_n)$ com $f = -\nabla L$, o que dá

$$\theta_{n+1} = \theta_n - h\,\nabla L(\theta_n).$$

Essa é exatamente a atualização da descida do gradiente, com a taxa de aprendizado fazendo o papel do passo $h$. Por isso, o que se sabe sobre o erro e a estabilidade do método de Euler ajuda a explicar o comportamento do treinamento.

## O que o notebook faz

O notebook `Projetofinal_EDO.ipynb` segue o raciocínio do trabalho em quatro partes:

1. **Método de Euler.** Resolve o fluxo de gradiente de uma função de erro quadrática, que tem solução exata, e compara a trajetória numérica com ela para três tamanhos de passo.
2. **Descida do gradiente.** Implementa o algoritmo de forma independente, sem usar o método de Euler, com o mesmo ponto de partida e o mesmo passo.
3. **Igualdade.** Compara as duas sequências e mostra que são iguais.
4. **Otimização na prática.** Ajusta uma reta a dados por regressão linear usando a descida do gradiente, mostrando a reta se aproximando dos pontos e o efeito de diferentes taxas de aprendizado.

## Principais resultados

- O método de Euler e a descida do gradiente produzem sequências exatamente iguais, inclusive quando o passo é grande demais e o método diverge.
- Na função de erro $L(\theta) = \frac{a}{2}\theta^2$ com $a = 10$, o passo 0,05 converge de forma suave, o passo 0,15 converge oscilando e o passo 0,25 diverge. O limite de estabilidade é $h < 2/a = 0{,}2$.
- Na regressão linear, a descida do gradiente com uma boa taxa de aprendizado chega ao mesmo resultado do método dos mínimos quadrados. Uma taxa muito pequena é lenta, e uma taxa acima do limite de estabilidade faz o erro explodir.
- Comparada com a solução precisa da equação diferencial, a descida do gradiente se afasta menos quando o passo diminui, com o erro caindo aproximadamente pela metade a cada vez que o passo é dividido por dois, o comportamento de primeira ordem esperado do método de Euler.

## Estrutura do repositório

| Arquivo | Descrição |
|---|---|
| `Projetofinal_EDO.ipynb` | Notebook com o código e os textos do projeto |
| `CapaEDO.png` | Capa do projeto |
| `LICENSE` | Licença do projeto |
| `README.md` | Este arquivo |

## Como executar

1. Baixe o repositório pelo botão verde **Code**, opção **Download ZIP**, e extraia a pasta.
2. Instale as bibliotecas usadas, com o comando abaixo no terminal:

```
   pip install numpy matplotlib scipy jupyter
```

   O `numpy` faz os cálculos numéricos, o `matplotlib` desenha os gráficos, o `scipy` resolve a equação diferencial com alta precisão na última parte e o `jupyter` permite abrir o notebook.
3. Abra o notebook `Projetofinal_EDO.ipynb` no Jupyter, no VS Code ou no Google Colab e execute as células **na ordem**, de cima para baixo. A ordem importa, porque cada célula usa o que foi definido nas anteriores.

O notebook não grava arquivos: os gráficos aparecem na própria tela, e os dados da regressão são gerados com uma semente fixa, então os resultados são os mesmos a cada execução.

## Referências

BOYD, S.; VANDENBERGHE, L. **Convex optimization**. Cambridge: Cambridge University Press, 2004. Disponível em: https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf. 

GOODFELLOW, I.; BENGIO, Y.; COURVILLE, A. **Deep learning**. Cambridge: MIT Press, 2016. Disponível em: https://www.deeplearningbook.org/. .

MÉTODO de Euler. In: FÍSICA COMPUTACIONAL. Porto Alegre: UFRGS, [s.d.]. Disponível em: https://fiscomp.if.ufrgs.br/index.php/M%C3%A9todo_de_Euler. 

SHIEBLER, D. Gradient descent is Euler's method. **Dan Shiebler**, 28 nov. 2020. Disponível em: https://danshiebler.com/2020-11-28-gradient-descent/. 

ANTHROPIC. **Claude Sonnet 5.5**. Modelo de linguagem de grande escala. [S. l.]: Anthropic, 2026. Disponível em: https://claude.ai. 

## Autores

<table>
  <tr>
     <td align="center">
      <a href="https://github.com/gabikbrown">
        <img src="https://github.com/gabikbrown.png" width="100" alt="Foto de Gabriela Cabral"><br>
        <sub><b>Gabriela Cabral</b></sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/acrsfloripa-prog">
        <img src="https://github.com/acrsfloripa-prog.png" width="100" alt="Foto de Arthur Cunha"><br>
        <sub><b>Arthur Cunha</b></sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/camilapangrassio">
        <img src="https://github.com/camilapangrassio.png" width="100" alt="Foto de Camila Pangrassio"><br>
        <sub><b>Camila Pangrassio</b></sub>
      </a>
    </td>
   
  </tr>
</table>

## Licença

Este projeto está licenciado sob a GPL-3.0. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

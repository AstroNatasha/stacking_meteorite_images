# Comparando técnicas de manipulação de imagens para a remoção da contaminação de elementos na superfície de meteoritos

## Resumo

Ao analisar a superfície do meteorito Pirenópolis pela técnica do Microscópio Eletrônico (MEV/SEM), temos acesso a várias imagens de uma mesma região específica na escala de 250 micrômetros. O microscópio eletrônico pode detectar diferentes elementos e associá-los a cores. Desta forma, podemos ter informações sobre como os elementos interagem entre si, possibilitando a identificação dos minerais presentes. Durante o processo de tratamento do meteorito, podem ocorrer contaminações de elementos na superfície. Identificamos estas contaminações por conta dos relevos apresentados na imagem. Neste caso, Temos contaminações de Carbono (C) na superfície e queremos removê-las. Este código apresenta uma comparação de 4 formas diferentes para realizar esta remoção. 

## Sobre o repositório

- ‘Fe.PNG’,‘Ni.PNG’,‘Al.PNG’,‘P.PNG’,‘C.PNG’: Imagens no formato PNG da mesma área de superfície do meteorito Pirenópolis, cada uma representando um elemento por uma cor diferente.
-  'full_image.PNG' : Imagem única no formato PNG da mesma área de superfície do meteorito Pirenópolis, com cada uma elemento sendo representado por uma cor diferente.

- ‘removing_pixels.ipynb’: Código em Python que realiza técnicas de remoção da contaminação

## Dependências

- NumPy
- Matplotlib
- cv2

## Como usar o código

Clone este repositório ou baixe o arquivo ‘removing_pixels.ipynb’para o seu ambiente de trabalho. Execute o código Python ‘removing_pixels.ipynb’ em seu ambiente. Você pode fazer isso usando um ambiente Python de sua escolha, como Jupyter Notebook ou um ambiente de desenvolvimento integrado (IDE).

Primeiro, certifique-se de que os arquivos de imagem estão presente no mesmo diretório que o arquivo Python. As bibliotecas devem estar instaladas em seu ambiente Python.

## Metodologia
### Solução 1 - Empilhar as imagens dos elementos
Com cada imagem representando um elemento, foi testada uma função que remove os pixels mais brilhantes definidos à partir de um determinado nível de brilho na imagem do carbono.

### Solução 2 - Identificar pixels mais brilhantes da imagem completa
Remover os pixels mais brilhantes da imagem completa é uma solução boa caso houvesse algum outro ponto de carbono na imagem que não fosse resultado de uma contaminação, porque neste caso a imagem é feita em relevo, de forma que as contaminações sempre serão os pixels mais brilhantes.

### Solução 3 - Identificar a cor azul da imagem completa
Esta solução consegue abranger casos em que não necessariamente queremos remover os pixels mais brilhantes, mas sim, um elemento por completo. Não é muito útil para casos de contaminação, mas certamente é interessante para isolar um elemento dos outros, caso quiséssemos tanto removê-los, quanto estudá-los separadamente (se não houvesse a opção de imagens separadas para cada elemento, este seria um bom começo).

### Solução 4 - Não empilhar as imagens dos elementos com Carbono
Claro, a solução mais simples se um elemento é exclusivamente uma contaminação, como é o caso dessa área do meteorito Pirenópolis.

## Conclusão
Das soluções, a Solução 2 é a mais eficiente para casos de contaminação, pois permite que apenas objetos contaminados sejam removidos, independente de existe o mesmo elemento que realmente percente à superfície do meteorito. Mesmo assim, em nenhuma solução houve remoção totalmente completa do carbono nas imagens, provavelmente porque as imagens não foram criadas com a ideia de uma manipulação posterior. Apesar disso, este é um projeto inicial escalável que tem potencial de sofisticação. Como passo futuro, talvez fosse interessante pensar em formas de quantizar os pixels removidos de forma que a contagem do elemento contaminador também pudesse ser removida, oferecendo uma análise ainda mais precisa.

## Referências


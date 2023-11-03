# Comparando técnicas de manipulação de imagens para a remoção da contaminação de elementos na superfície de meteoritos

## Resumo

O meteorito Pirenópolis é um meteorito metálico pouco estudado que possui uma matriz composta por aproximadamente 95% de Fe e cerca de 5% de Ni (Kamacita), com regiões de (Fe, Ni) 3P (Shreibersita), nanopartículas de C e traços de Al e Si. A análise mineralógica e elementar do mesmo foi realizada por duas técnicas não-destrutivas, PIXE (Emissão de Raios-X Induzidos por Partículas) e MEV (Microscopia Eletrônica de Varredura). Ao analisar a superfície do meteorito pela técnica de Microscopia Eletrônica de Varredura (MEV/SEM), tivemos acesso a várias imagens de uma mesma região específica na escala de 250 micrômetros. O microscópio eletrônico pode detectar diferentes elementos e associá-los a cores. Desta forma, podemos ter informações sobre como os elementos interagem entre si, possibilitando a identificação dos minerais presentes. Durante o processo de tratamento do meteorito, podem ocorrer contaminações de elementos na superfície do mesmo. Identificamos estas contaminações por conta dos relevos apresentados na imagem completa (full_image.PNG) . Neste caso, Temos contaminações de Carbono (C) na superfície e queremos removê-las. Este código apresenta uma comparação de 4 formas diferentes para realizar esta remoção. No fim, transformamos a imagem no formato fits.

## Sobre o repositório

- ‘Fe.PNG’,‘Ni.PNG’,‘Al.PNG’,‘P.PNG’,‘C.PNG’: Imagens no formato PNG da mesma área de superfície do meteorito Pirenópolis, cada uma representando um elemento por uma cor diferente.
-  'full_image.PNG' : Imagem única no formato PNG da mesma área de superfície do meteorito Pirenópolis, com cada uma elemento sendo representado por uma cor diferente.

- ‘removing_pixels.ipynb’: Código em Python que realiza técnicas de remoção da contaminação

## Dependências

- numpy
- matplotlib
- cv2
- Astropy.io
- PIL

## Como usar o código

Clone este repositório ou baixe o arquivo ‘removing_pixels.ipynb’para o seu ambiente de trabalho. Execute o código Python ‘removing_pixels.ipynb’ em seu ambiente. Você pode fazer isso usando um ambiente Python de sua escolha, como Jupyter Notebook ou um ambiente de desenvolvimento integrado (IDE).

Primeiro, certifique-se de que os arquivos de imagem estão presente no mesmo diretório que o arquivo Python. As bibliotecas devem estar instaladas em seu ambiente Python.

## Metodologia
### Solução 1 - Empilhar as imagens dos elementos
Com cada imagem representando um elemento, foi testada uma função que remove os pixels mais brilhantes definidos à partir de um determinado nível de brilho na imagem do carbono.

### Solução 2 - Identificar pixels mais brilhantes da imagem completa
Remover os pixels mais brilhantes da imagem completa é uma solução boa caso houvesse algum outro ponto de carbono na imagem que não fosse resultado de uma contaminação, porque neste caso a imagem é feita em relevo, de forma que as contaminações sempre serão os pixels mais brilhantes.

### Solução 3 - Identificar a cor azul da imagem completa
Esta solução consegue abranger casos em que não necessariamente queremos remover os pixels mais brilhantes, mas sim, um elemento por completo. Não é muito útil para casos de contaminação, mas certamente é interessante para isolar um elemento dos outros, caso quiséssemos tanto removê-los, quanto estudá-los separadamente (se não houvesse a opção de imagens separadas para cada elemento, este seria um bom começo). Mesmo testando a definição de diferentes faixas de azul em HSV e BGR, ainda sim houve um problema em que tons de verde também foram removidos, então este é um ponto a se melhorar.

### Solução 4 - Não empilhar as imagens dos elementos com Carbono
Claro, a solução mais simples se um elemento é exclusivamente uma contaminação, como é o caso dessa área do meteorito Pirenópolis.

## Conclusão
Das soluções, a Solução 2 é a mais eficiente para casos de contaminação, pois permite que apenas objetos contaminados sejam removidos, independente de existe o mesmo elemento que realmente percente à superfície do meteorito. Mesmo assim, em nenhuma solução houve remoção totalmente completa do carbono nas imagens, provavelmente porque as imagens não foram criadas com a ideia de uma manipulação posterior. Apesar disso, este é um projeto inicial escalável que tem potencial de sofisticação. Como passo futuro, talvez fosse interessante pensar em formas de quantizar os pixels removidos de forma que a contagem do elemento contaminador também pudesse ser removida, oferecendo uma análise ainda mais precisa.

## Referências
FONSECA, Natasha Costa da et al.. ANÁLISE ELEMENTAR DOS METEORITOS PIRENÓPOLIS E SANTA CATARINA.. In: Anais da Jornada Giulio Massarani de Iniciação Científica, Tecnológica, Artística e Cultural. Anais...Rio de Janeiro(RJ) UFRJ, 2021. Disponível em: https//www.even3.com.br/anais/jgmictac/318413-ANALISE-ELEMENTAR-DOS-METEORITOS-PIRENOPOLIS-E-SANTA-CATARINA. Acesso em: 03/11/2023

JARRELL, Karícia Fraga Godoy. Análise elementar dos meteoritos Santa Vitória do Palmar e Cebollati. 2019. 110 f. Trabalho de conclusão de curso (Bacharelado em Astronomia) - Observatório do Valongo, Universidade Federal do Rio de Janeiro, Rio de Janeiro, 2019.

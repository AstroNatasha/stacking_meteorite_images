# Comparing Image Manipulation Techniques for the Removal of Contaminants on the Surface of Meteorites (with Python)

## Abstract

The Pirenópolis meteorite is a poorly studied metallic meteorite with a matrix composed of approximately 95% Fe and about 5% Ni (Kamacite), featuring regions of (Fe, Ni)3P (Shreibersite), C nanoparticles, and traces of Al and Si. Mineralogical and elemental analysis was conducted using two non-destructive techniques, PIXE (Particle-Induced X-ray Emission) and SEM (Scanning Electron Microscopy). By analyzing the meteorite's surface through Scanning Electron Microscopy (SEM), we obtained multiple images of a specific region at a scale of 250 micrometers. The electron microscope can detect different elements and associate them with colors, providing insights into element interactions for mineral identification. During the meteorite treatment process, surface contamination of elements can occur. Contaminations were identified through relief features in the complete image ('full_image.PNG'). In this case, we have Carbon (C) contaminations on the surface that need removal. This code presents a comparison of four different methods for performing this removal, ultimately transforming the image into fits format.

## About the Repository

- 'Fe.PNG', 'Ni.PNG', 'Al.PNG', 'P.PNG', 'C.PNG': PNG format images of the same surface area of the Pirenópolis meteorite, each representing an element by a different color.
- 'full_image.PNG': Single PNG image of the same surface area of the Pirenópolis meteorite, with each element represented by a different color.
- 'removing_pixels.ipynb': Python code performing contamination removal techniques.

## Dependencies

- numpy
- matplotlib
- cv2
- Astropy.io
- PIL

## How to Use the Code

Clone this repository or download the 'removing_pixels.ipynb' file to your working environment. Run the 'removing_pixels.ipynb' Python code in your environment, such as Jupyter Notebook or an integrated development environment (IDE) of your choice.

First, ensure that the image files are present in the same directory as the Python file. The required libraries must be installed in your Python environment.

## Methodology
Para manipular as imagens, é necessário transformá-las em arrays, de forma que temos matrizes de pixels. Esta é uma prática muito importante na astronomia, uma vez que lidamos bastante com imagens e é comum precisar tratá-las para obter análises específicas. As soluções apresentadas são exemplos dessas manipulações.

### Solution 1 - Stack images of the elements
Each image representing an element was tested with a function that removes the brightest pixels defined from a certain brightness level in the carbon image.

### Solution 2 - Identify brightest pixels in the complete image
Removing the brightest pixels from the complete image is a good solution if there were other carbon points in the image not resulting from contamination. In this case, the image is relief-based, so contaminations will always be the brightest pixels.

### Solution 3 - Identify the blue color in the complete image
This solution covers cases where we do not necessarily want to remove the brightest pixels but an entire element. It may not be very useful for contamination cases but is suitable for isolating one element from others, useful for removal or separate study (if there were no separate images for each element, this would be a good start). Even testing the definition of different blue ranges in HSV and BGR, there was still an issue where green tones were also removed, so there is room for improvement.

### Solution 4 - Do not stack images of elements with Carbon
Of course, the simplest solution if an element is exclusively contamination, as is the case with this area of the Pirenópolis meteorite.

## Conclusion
Of the solutions, Solution 2 is the most efficient for contamination cases, allowing only contaminated objects to be removed, regardless of whether the same element actually belongs to the meteorite's surface. Still, in no solution was the complete removal of carbon in the images achieved, probably because the images were not created with the idea of later manipulation. Despite this, this is an initial scalable project with the potential for sophistication. As a future step, it might be interesting to think about ways to quantize the removed pixels so that the count of the contaminating element could also be removed, offering an even more accurate analysis.

## References
FONSECA, Natasha Costa da et al.. ANÁLISE ELEMENTAR DOS METEORITOS PIRENÓPOLIS E SANTA CATARINA.. In: Anais da Jornada Giulio Massarani de Iniciação Científica, Tecnológica, Artística e Cultural. Anais...Rio de Janeiro(RJ) UFRJ, 2021. Disponível em: https//www.even3.com.br/anais/jgmictac/318413-ANALISE-ELEMENTAR-DOS-METEORITOS-PIRENOPOLIS-E-SANTA-CATARINA. Acesso em: 03/11/2023

JARRELL, Karícia Fraga Godoy. Análise elementar dos meteoritos Santa Vitória do Palmar e Cebollati. 2019. 110 f. Trabalho de conclusão de curso (Bacharelado em Astronomia) - Observatório do Valongo, Universidade Federal do Rio de Janeiro, Rio de Janeiro, 2019.

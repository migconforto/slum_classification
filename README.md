# Images
Link para as Imagens: [images](https://drive.google.com/drive/folders/1qlA6vpzEmykIpxV55fhSHC_tE-KNYxhD?usp=sharing)

# Masks
Link para as máscaras: [masks](https://drive.google.com/drive/folders/1xT5Xke3cLmfi-Lqu6SQdU5dPWo9GnxwG?usp=sharing)

# Resumo dos resultados
Favelas e comunidades urbanas possuem uma dinâmica própria de expansão e esta dinâmica traz consigo
uma demanda por políticas públicas específicas para essas áreas. Para garantir políticas públicas adequadas 
é importante acompanhar as modificações ocorridas ao longo do tempo, 
inclusive a sua expansão ou retração. O trabalho propõe o uso de múltiplas técnicas e algoritmos de 
machine learning para a identificação de favelas e comunidades urbanas do bairro da Pavuna, na cidade
do Rio de janeiro, além de avaliar a possibilidade de expandir a aplicação para outras áreas do município.  

Para possibilitar a utilização de classificadores supervisionados, foi criada uma amostra de
treinamento, composta por polígonos que delimitam elementos de interesse, os quais sejam
aqueles característicos de favelas e comunidades urbanas. Tais polígonos foram desenhados
em setores censitários classificados pelo IBGE como aglomerados subnormais.
Os setores foram selecionados por amostragem inversa até alcançarem 30% do total
de setores desse tipo. Para a composição das unidades da amostra foi utilizada a 
ferramenta Quantum GIS. Cada polígono é a classificação de quais áreas
dentro do setor especificado são consideradas favelas ou comunidades urbanas. A amostra criada é vista na imagem abaixo.

![Imagem de satélite e máscara](https://github.com/migconforto/pavuna_ahs/blob/main/images/Image_orig.jpeg)


O pré-processamento da imagem utiliza algoritmos baseados em segmentação de superpixel pelos métodos de Felzenszwalbs e SLIC, 
adicionando a média, mediana e desvio padrão das bandas para cada método de superpixel à imagem original. Além da adição de medidas 
representativas das distribuições espectrais dos superpixels, foi o índice de forma espacial (SSI) à imagem original, totalizando 
sete novas características além do RGB natural da imagem.

Os seguintes algoritmos foram selecionados para teste: LightGBM, MLP Classifier, Random Forest, Gradient Boosting, K-Means, 
Naive-Bayes e Logistic-regression. A seleção dos melhores parâmetros para cada modelo foi feita através do método
[GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html) da scikit-learn. 
Os resultados para cada classificador podem ser observados na imagem e tabela abaixo.

![Predição dos modelos finais](https://github.com/migconforto/pavuna_ahs/blob/main/images/models_pred.png)


| Model | Accurracy | Precision | Recall | F1-Score | IoU |
|---|---|---|---|---|---|
| Gradient Boost | 93.5% | 80.6% | 71.6% | 75.8% | 66.4% |
| Light GBM | 87.2% | 53.6% | 76.3% | 63.0% | 62.3% |
| MLP Classifier | 90.6% | 65.4% | 73.2% | 69.1% | 53.3% |
| Random Forest | 85.4% | 48.9% | 49.5% | 49.2% | 58.4% |
| Naive-Bayes | 62.0% | 22.2% | 66.1% | 33.2% | 50.6% |
| K-Means | 53.3% | 15.0% | 48.7% | 23.0% | 54.2% |
| Logistic-Regression | 85.4% | 47.5% | 17.0% | 25.1% | 51.0% |

Link para as Imagens: [images](https://drive.google.com/drive/folders/1qlA6vpzEmykIpxV55fhSHC_tE-KNYxhD?usp=sharing)
Link para as máscaras: [masks](https://drive.google.com/drive/folders/1xT5Xke3cLmfi-Lqu6SQdU5dPWo9GnxwG?usp=sharing)

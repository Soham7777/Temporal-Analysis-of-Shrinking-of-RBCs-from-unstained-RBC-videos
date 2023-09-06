# Temporal Analysis of Shrinking of RBCs from Unstained RBC Videos

## Data Section

The dataset, collected from KMC Physiology Department, consists of videos of RBCs stressed with UREA, NACL, and SUCROSE. This dataset is crucial for observing the reactions of normal blood cells when exposed to disease-related foreign bodies, aiding in drug manufacturing for medicinal use.

**Data Processing after Annotations**

Around 100 images were annotated using LabelMe, focusing on the UREA stress category, totaling approximately 150-200 cells in these annotated images. The annotations were converted to JSON format and further transformed into PNG files to be used as ground truth.

## Segmentation Models Library

This library offers pre-defined functions, including Jaccard loss and Intersection over Union (IoU) metrics, specifically designed to handle data imbalance and evaluate models accurately. The library provides various pre-trained backbones for the encoder part of the architecture, enhancing convergence speed through the use of ImageNet-trained weights.

### Best Model Results 
    

**Real Image** ![](https://github.com/Soham7777/Customer-Segmentation-Using-ML/assets/66548809/aa1dcc24-a76b-4add-912d-d7e832c0831b) 


**Predicted Image** ![](https://github.com/Soham7777/Temporal-Analysis-of-Shrinking-of-RBCs-from-unstained-RBC-videos/assets/66548809/25886189-7867-4c13-82f1-0d7a87c8d290)


## Conclusion

### U-Net Architecture

The initial experiment with the traditional U-Net architecture yielded unsatisfactory results due to inappropriate loss functions and metrics, resulting in the model's inability to predict anything on the test dataset.

### Segmentation Models Library with U-Net

Implementing the Segmentation Models Library with the original U-Net model, weighted binary cross-entropy loss, and Jaccard loss, along with IoU scoring, improved model performance. However, after 125 epochs, the model stopped learning, and some target cells were missing in the predicted masks.

### Inception v3 as Backbone

Incorporating Inception v3 as the backbone achieved the highest IoU score among all models. Loss convergence occurred quickly, around 25-30 epochs, with accurate predicted masks that included all target cells. This model proved to be the best for the current dataset.

## Installation steps
- `!pip install segmentation_models`
- `Install LabelME for annonations : https://pypi.org/project/labelme/`
  
## References

- Segmentation Library: [Segmentation Models Library](https://github.com/qubvel/segmentation_models)
- Data Modeling and Base U-Net Architectures: [Python for Microscopists](https://github.com/bnsreenu/python_for_microscopists)

## Extra Work

The dataset used was the Oxford Pet Dataset, consisting of 37 categories with various cat and dog breeds. Although the model showed convergence and produced masks resembling the test images, some features were still missing. Further improvements may require hyperparameter tuning and more extensive dataset exploration.

Link to Colab: [Google Colab Notebook](https://colab.research.google.com/drive/1L8xqBGISayV6yBdoeVJbQmWRiJ9PAWw3?usp=sharing)

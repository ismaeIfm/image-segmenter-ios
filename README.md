# Image Segmenter ios
Core ML Image Segmentation on ios
 

## Examples
<img src="Resources/Example.jpg" width="100%" >


## mlmodel
Core ML model file are converted from <a href="https://github.com/tensorflow/models/blob/master/research/deeplab/g3doc/model_zoo.md">deeplab MobileNetv2</a>
### Example
Download checkpoint and uncompress it
```bash
wget http://download.tensorflow.org/models/deeplabv3_mnv2_pascal_trainval_2018_01_29.tar.gz
tar xvf deeplabv3_mnv2_pascal_trainval_2018_01_29.tar.gz
```

Then convert to mlmodel with tfcoreml
```python
import tfcoreml as tf_converter 
tf_converter.convert(
    tf_model_path = 'deeplabv3_mnv2_pascal_trainval/frozen_inference_graph.pb', 
    mlmodel_path = 'Deeplab.mlmodel', 
    image_input_names=["ImageTensor:0"], 
    output_feature_names = ['ResizeBilinear_3:0'], 
    input_name_shape_dict = {'ImageTensor:0' : [1, 513, 513, 3]}, 
    use_coreml_3 = False) 

```
## Usage
 

```swift
 let sourceImg = UIImage.init(named: "test.jpg")!
 let segmentImg = sourceImg.segmentation()
```

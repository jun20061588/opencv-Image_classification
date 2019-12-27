# Pelee opencv-Image_classification
Pelee model is now supported 

# opencv-Image_classification
Train Image classification on CIFAR10 using tensorflow and keras. 
Create a inference using opencv. OpenCV to read tensorflow graph.

## Train:
python3 train.py

## Reduce unwanted nodes:
python3 optimize_for_inference.py --input model1.pb --output opt_model1.pb --input_names input_1 --output_names predictions/Softmax

## Convert to .pbtxt 
python3 to_pbtxt.py

## remove nodes with names flatten/Shape, flatten/strided_slice, flatten/Prod, flatten/stack.

## Replace a node 
node { name: "flatten/Reshape" op: "Reshape" input: "block5_pool/MaxPool" input: "flatten/stack" }

by

node { name: "flatten/Reshape" op: "Flatten" input: "block5_pool/MaxPool" }

## Test 
python3 test.py

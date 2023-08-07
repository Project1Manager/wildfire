# wildfire
Wildfire Recognition AI

## Resources Used
https://www.kaggle.com/datasets/mohnishsaiprasad/forest-fire-images

## Algorithm
This forest fire recognition AI uses Imagenet in order to identify common signs of fire, such as red and orange flames as well as thick dark grey/black smoke. uses my trained model to determine whether it is a forest fire or not, before sorting the assigned image into one of two classifications; forest fire or forest. It then outputs the image that it was assigned as well as the determintation on whether it is a fire or not, followed by how certain it is on the determination.

## Running this project.
Requirements
1. Jetson Nano
2. USBC Power Supply
3. Wifi USB Dongle (w/ an optional USB extension cable for the dongle)

Directions
1. Update the board with: sudo apt-get update & sudo apt-get install git cmake
2. cd back to home
3. Download the jetson-inference library: git clone --recursive https://github.com/dusty-nv/jetson-inference || cd jetson-inference || git submodule update --init
4. install python3: sudo apt-get install libpython3-dev python3-numpy
5. Change to Jetson Inference: cd jetson-inference
6. Make a build directory: mkdir build
7. Go into build. cd build
8. Download resnet: cmake ../
9. Run the tools that train will use later. make || sudo make install || sudo ldconfig
10. Get out of build, then cd into classification. cd .. || cd python/training/classification
11. Download the resnet18.onnx file in this project, cd into models and put it in models/forestfire. cd models || mkdir forestfire
12. Download the images and put it anywhere in classification, not in the models folder nor the forestfire folder.
13. Download the labels.txt file and put it anywhere in classification.
14. Run the command to use the resnet file to classify your images. imagenet --model=models/forestfire/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=(filepath)/labels.txt (filepath)/(image/folder) (output location) ||| MAKE SURE THAT YOU REPLACE PARTS OF THE COMMAND WITH YOUR FILEPATH, IMAGE/FOLDER AND OUTPUT LOCATION OR THIS COMMAND WILL NOT WORK. THIS COMMAND IS RUN IN THE classification DIRECTORY.
15. EXAMPLE COMMAND: imagenet --model=models/forestfire/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/forestfire/labels.txt data/forestfire/test/forest_fire/ data/forestfire ||| This command, if you used the same filepath as I did, will output the entire folder, and not just one image. To output just one image, specify the image name after the folder. 

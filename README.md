# Code for Training MNIST along with a Random Number
## Objective
The objective of the code is to take 2 inputs:<br />
  1. an image from the MNIST dataset (say 5), and<br />
  2. a random number between 0 and 9, (say 7)<br />

And give two outputs:
  1. the "number" that was represented by the MNIST image (predict 5), and<br />
  2. the "sum" of this number with the random number and the input image to the network (predict 5 + 7 = 12)<br />

## Approach
The entire approach to reach the objective has been done through following steps:
  1. **Understanding and Visualing the Data**<br />
    a. Downloading the MNIST Data<br />
    b. Visualising the Data<br />
    c. Trying out Batch Creation <br />
  2. **Creating Dataset** for training **with 2 Inputs and 2 Labels**<br />
    a. MNIST Data from the standard dataset was loaded (Train Data Size: 60,000 and Test Data Size: 10,000)<br />
    b. Defining a separate class (with parent class Dataset of torch) to create Random Number Datatset with one hot encoding as Input Data and Number as ouptut<br />
      - Same Size Test and Train Data was created <br />
  3. Defining **Dataset class for getting inputs for model training**<br />
    a. Takes input of MNIST Dataset and Random Number Dataset<br />
    b. Returns a dataset which can be used to solve this problem<br />
  4. Creating **Training and Testing Dataloader** for model training <br />
  5. **Defining Network**:<br />
    a. Network has been specifically designed keeping in mind that a **receptive field of 11** is reached before sending data to **transition block**<br />
    b. Convolving till reaching size of kernel 512*3*3<br />
    c. One Fully Connected layer before output layer of MNIST data<br />
    d. Concatenating MNIST one hot vector output with random number one hot vector<br />
    e. Passed through one fully connected layer before final output layer<br />
  6. Defining **function to get correct number of predictions**<br />
  7. **Train and Test Loader** were created<br />
  8. **Checking of Network** for one step of one epoch - to understand if there is any problem in Network Defined<br />
    a. Reitertaed till Network was finalised and running smoothly<br />
  9. **Model Training** - Model was trained for 10 epochs with Training Data (Number of epochs could have been more optimised based on Training Loss - but not implemented in this code) <br />
  10. **Model parameters were saved** on drive<br />
  11. **Running test data using saved model**<br />
  
## Output
  Received **final accuracy of 99.02 % for Test data** for both *MNIST* and *Sum of MNIST ouput and Random Number*<br />

## Training Log
```
epoch: 1 Train tot_corr MNIST %: 92.75166666666667 Train loss MNIST: 212.84286183165386 Train tot_corr Sum %: 68.93833333333333 Train loss Sum: 1439.8937289714813
epoch: 2 Train tot_corr MNIST %: 98.02166666666666 Train loss MNIST: 62.28390231949743 Train tot_corr Sum %: 98.02166666666666 Train loss Sum: 235.9421487338841
epoch: 3 Train tot_corr MNIST %: 98.64166666666667 Train loss MNIST: 42.35233556997264 Train tot_corr Sum %: 98.64166666666667 Train loss Sum: 120.22995690070093
epoch: 4 Train tot_corr MNIST %: 98.92333333333333 Train loss MNIST: 32.93829559401638 Train tot_corr Sum %: 98.92333333333333 Train loss Sum: 92.19452646374702
epoch: 5 Train tot_corr MNIST %: 99.08833333333334 Train loss MNIST: 28.46076342613378 Train tot_corr Sum %: 99.08833333333334 Train loss Sum: 75.8768017962575
epoch: 6 Train tot_corr MNIST %: 99.28166666666667 Train loss MNIST: 23.416712078877026 Train tot_corr Sum %: 99.28166666666667 Train loss Sum: 60.28840802796185
epoch: 7 Train tot_corr MNIST %: 99.31 Train loss MNIST: 20.664671138230005 Train tot_corr Sum %: 99.31 Train loss Sum: 56.641787603497505
epoch: 8 Train tot_corr MNIST %: 99.37 Train loss MNIST: 18.97374286950162 Train tot_corr Sum %: 99.37 Train loss Sum: 51.20052558043972
epoch: 9 Train tot_corr MNIST %: 99.51666666666667 Train loss MNIST: 16.290747231671958 Train tot_corr Sum %: 99.51666666666667 Train loss Sum: 42.12957690563053
epoch: 10 Train tot_corr MNIST %: 99.60833333333333 Train loss MNIST: 12.63197883257476 Train tot_corr Sum %: 99.60833333333333 Train loss Sum: 33.237089331727475
```

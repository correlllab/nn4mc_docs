Tutorials
==========


Using Generated Code
======================

Arduino
--------

First, open a new sketch in Arduino, then, open all the files that were generated using nn4mc in Arduino.

The following code is an example of what it would take to get `nn4mc` to work on your Arduino code. In this example, we allocate and send to the neural network an input of ones. This code looks as follows:

First, create the prototypes for the functions that we will be using from `nn4mc`:

::

  void buildLayers();
  float * fwdNN(float* data);


In the setup function after we begin our serial port, we call the function `buildLayers()`. This function will initialize all the layers and create the necessary components for our feed forward.

::

  void setup() {
      Serial.begin(115200); // feel free to adjust this as desired
      buildLayers();

  }

In the loop function, after we collect our input, we call `fwdNN(input)`, which is the function that will output a pointer. This pointer will contain the output data from the neural network. You can access this output as a regular array, for example, output[0] indicates the first element in the output layer and so forth. In the following example, we have a neural network whose input layer is is of size `(None, 10, 1)` and output size `(3)`.

::

  void loop() {

        float * input= (float*)malloc(10*sizeof(float));
        for (int i=0; i<10; i++) input[i] = 1.0;

        float * output;

        output = fwdNN(input);

        for (int i=0; i<3; i++) {
            Serial.print(output[i]);
            Serial.print(" ");
        }

        Serial.println();

        free(output); // output needs to be freed for best performance. Please do not free input.
        delay(1);
      }

Testing Instructions
=====================

Arduino
-------

You can start with a trained Keras file, run it through ``nn4mc`` using the instructions above and import the code in Arduino. Make sure you test the specific layers. Use ``loadModel.py`` under data to compare against the actual Keras results/outputs at specific places within the neural network. We usually test the performance of the layer by sending an array of ones as input to the neural newtork and seeing how faithful the results should be. There should be a 1:1 fidelity with those
results since both languages use float32 (Arduino serial monitor sometimes rounds the numbers, so you could just print the first 16 digits for the number or something like that). Whatever the result of the test is, write a new issue with the following template:

::

    FILE: filename.cpp
    RESULT: passing/failing/need_further_test
    TEST TYPE: Unit test/Integration test
    DESCRIPTION:

    input:
    output:
    desired output:
    NOTES:
    [write additional notes here]

    RECOMMENDATIONS:
    [write specific template fixes that you think might fix it (optional)]

Please do not try to modify source code or template codes, but if you find an error in the templates make sure to add it as a recommendation.


ESP-IDF
-------

[TBD]

About
=====

Why nn4mc?
----------

`nn4mc` bridges the gap between high level neural network training in fully capable PCs and microcontrollers.

 We present a library to automatically embed signal processing and neural network predictions into the material robots are made of. Deep and shallow neural network models are first trained offline using state-of-the-art machine learning tools and then transferred onto general purpose microcontrollers that are co-located with a robot's sensors and actuators. We validate this approach using multiple examples: a smart robotic tire for terrain classification, a robotic finger sensor for
 load classification and a smart composite capable of regressing impact source localization. In each example, sensing and computation are embedded inside the material, creating artifacts that serve as stand-in replacement for otherwise inert conventional parts. The open source software library takes as inputs trained model files from higher level learning software, such as Tensorflow/Keras, and outputs code that is readable in a
 microcontroller that supports C. We compare the performance of this approach for various embedded platforms. In particular, we show that low-cost off-the-shelf microcontrollers can match the accuracy of a desktop computer, while being fast enough for real-time applications at different neural network configurations. We provide means to estimate the maximum number of parameters that the hardware will support based on the microcontroller's specifications.


 .. Note about Tensorflow 2.0:
 .. =============================================

 Make sure that the first layer in the neural network specifies the `input_shape` field when using Tensorflow 2.0 in order to get an appropriately functioning result.


 .. Citing nn4mc:
 .. =============


 ::

    Aguasvivas Manzano, Sarah, et al. “Embedded Neural Networks for Robot Autonomy.” International Symposium on Robotics Research, 2019.

 Or

 ::

    Manzano, S. A., Hughes, D., Simpson, C., Patel, R., & Correll, N. (2019). Embedded Neural Networks for Robot Autonomy. arXiv preprint arXiv:1911.03848.

 Or

 ::

    @misc{nn4mc,
            title={Embedded Neural Networks for Robot Autonomy},
            author={Sarah Aguasvivas Manzano and Dana Hughes and Cooper Simpson and Radhen Patel and Nikolaus Correll},
            year={2019},
            eprint={1911.03848},
            archivePrefix={arXiv},
            primaryClass={cs.RO}
        }

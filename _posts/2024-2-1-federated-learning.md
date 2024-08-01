---
layout: post
title: Improving Machine Learning lifecycle to preserve data privacy
subtitle: How Federated Learning preserves data privacy
gh-repo: naiborhujosua/Blog_Notes
gh-badge: [star, follow]
share-img: /assets/img/serverml.gif
tags: [machine learning,federated learning]
comments: true
mathjax: true
---



Big data has become ubiquitous, as every action we undertake generates data that holds the potential for valuable insights. For instance, we can improve our health management activities based on our sports activities tracked on our smartphones or we can type faster in the case of text generation while texting on our smartphones as well. These data or queries are one of many factors that need to preserve while we want to use them for machine learning use cases aforementioned. Data Privacy has been a big issue for big tech companies lately. There is a concern related to how big tech companies collect and use the data. For the purpose of this problem, there is a continuously developed framework that would be able to preserve data privacy while maintaining a machine learning model called Federated Learning.

![Federated ML](/assets/img/federatedml.jpg)  

## Introduction to Federated Learning

In a traditional way of training machine learning model, we are hosting the data and machine learning model on the same devices or centralized machine learning. However, Federated Learning learns a different way of training machine learning models with the data. Instead of sending data into the server to train, the model from the server is sent to each device.

![Federated ML](/assets/img/genmlfedml.png)


{: .box-note}
So, How could the ML model learns the data?

![source is via Cloudera blog](/assets/img/serverml.gif) 

The ML model does train the data for the available devices(node in the visualization above) whether when it is on idle mode/plugging or not used, so the user does not realize that the data has been trained by the machine learning model on the device. Then, a subset of devices that have already trained the data will aggregate the result to be sent to the server while also maintaining data privacy. This technology has been a breakthrough for maintaining data privacy which has been an issue for a few years while collecting and using data from users. Fortunately, Google has developed a TensorFlow federated learning API that we can use to implement federated learning when using TensorFlow for building machine learning applications. For anyone interested in the implementation of TensorFlow can look at the implementation code.

Google Colaboratory
[Federated ML on Google](https://colab.research.google.com/github/tensorflow/federated/blob/master/docs/tutorials/federated_learning_for_text_generation.ipynb)

Moreover, Google developed Gboard typing based on learning the data that is typed by users so that a few sentences can be used to predict the complete address available on google maps. You can see the visualization as follow. This prediction is without sending the data into the server first to get a better prediction but the machine learning model has learned the data to predict it. This is really a breakthrough in maintaining data privacy.

![Federated ML](/assets/img/googleml.gif)


### Federated Learning in Math

![Federated Work in Math](/assets/img/mlwork.jpg)


Federated Learning does train the data on each device and aggregates the results to update the global model by using optimizers like SGD or Adam optimizer (in the case of Neural Network to reach convergence) where the updated parameters/weights will be used again to train the data on each device. This process is repeated again and again to improve the metrics based on problems.

## Conclusion

Federated learning has been a good idea to be carried out in various machine learning projects. The idea of preserving data privacy can ensure the ease of machine learning projects in broader industries such as medicine, logistics, telecommunication, and insurance. I also see a handful of frameworks available to implement federated learning which means the existence of this framework will bring a brighter future for developing machine learning applications while also maintaining data privacy. If you browse through GitHub focusing on topics related to federated learning, you will uncover numerous stars awarded to this project.

References :

- [Practical Secure Aggregation for Privacy-Preserving Machine Learning](https://eprint.iacr.org/2017/281.pdf)

- [Federated Learning: Machine Learning on Decentralized Data (Google I/O’19)](https://www.youtube.com/watch?v=89BGjQYA0uE)

- [Towards Federated Learning at Scale: System Design](https://arxiv.org/abs/1902.01046)


Thank you for reading!

I really appreciate it 🤗. I post machine learning and deep learning- related topics. I try to keep my posts simple but precise, always providing visualization, and simulations.


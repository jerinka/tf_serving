-Original repo: [Link](https://neptune.ai/blog/how-to-serve-machine-learning-models-with-tensorflow-serving-and-docker)

####  [TensorFlow Serving](https://www.tensorflow.org/tfx/guide/serving) to serve an image classifier model 


To run this application, clone the repo:

```bash
 git clone https://github.com/jerinka/tf_serving.git
 cd tf_serving
 pip install -r requirements.txt
```

Install Tensorflow Serving
- [Link](https://www.tensorflow.org/tfx/serving/setup)



Start TF serving server
```
docker run -p 8501:8501 --name tfserving_classifier --mount type=bind,source=$PWD/weights/mnist/,target=/models/img_classifier -e MODEL_NAME=img_classifier -t tensorflow/serving
```

Kill previous server contaier
```
docker stop 08dbe5b60fabeb0ec9a33c2396c4e607b4b25ed61b16803b7cf4824a6b7dcfca
docker rm 08dbe5b60fabeb0ec9a33c2396c4e607b4b25ed61b16803b7cf4824a6b7dcfca
```

To make predictions, send HTTP request to server from another terminal.

```
  python predict.py
```

**Extra:**

To retrain the model, run the `python train.py`

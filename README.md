####  [TensorFlow Serving](https://www.tensorflow.org/tfx/guide/serving) to serve an image classifier model 


To run this application, clone the repo:

```bash
 git clone https://github.com/jerinka/tf_serving.git
 cd tf_serving
 pip install -r requirements.txt
```

Install Tensorflow Serving
- [Link](https://www.tensorflow.org/tfx/serving/setup)


Kill previous server contaier
```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```

Start TF serving server
```
docker run -p 8501:8501 --name tfserving_classifier --mount type=bind,source=$PWD/weights/mnist/,target=/models/img_classifier -e MODEL_NAME=img_classifier -t tensorflow/serving
```

To make predictions, send HTTP request to server from another terminal.

```
  python predict.py
```

**Extra:**

To retrain the model, run the `python train.py`

# container-from-scratch-python

This is building a container from scratch project. It is an exercise from the book [Cloud Computing for Data Analysis](https://noahgift.com/publication/cloud4data/)

## To build the container and push to Docker Hub

### Build image

Run the following command to build an image:

```bash
docker build --tag=${TAG_NAME} .
```

Note: the `TAG_NAME` must match the `<hub-user>/<repo-name>[:<tag>]` format.

Check it was created running:

```bash
docker image ls
```

### Run image

To run the image, do the following:

```bash
docker run -it ${TAG_NAME} python app.py --name "foo"
```

And you should see the foo as output.


### Push image to Docker Hub

You should create a public Docker Hub repo first and push it to your own.
In my case, [the repo](https://hub.docker.com/repository/docker/jeancarlo/simple-python-app) is `jeancarlo/simple-python-app`.

```bash
docker push ${TAG_NAME}
```

## Pulling from Docker Hub

To pull this image pulling from the Docker Hub, run the following:

```bash
docker pull jeancarlo/simple-python-app:0.0.1
docker run -it jeancarlo/simple-python-app bash
```

Then run:

```bash
python app.py  --help
```

To see if its ok. Then, to run the app:

```bash
docker run -it jeancarlo/simple-python-app --name "foo"
# The output
Hello foo!
```

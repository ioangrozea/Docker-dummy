# Dummy project that can be cloned and played around with

Project consists of 2 directories. Both have more or less teh same Dockerfile, the main difference being the base image.
The image build from the airflow image is not working as expected in regard to the cache.
When updating the poetry pyproject.toml file all dependencies are downloaded, but in the image build upon a simple 
python image it all works as expected. A more detailed description can be found [here](https://stackoverflow.com/questions/73650173/poetry-and-buildkit-mount-type-cache-not-working-when-building-over-airflow-imag?stw=2).

# How to use

1) install poetry: `pip install poetry==1.1.15`
2) move to each directory and run `DOCKER_BUILDKIT=1 docker build --progress=plain -t airflow-test -f Dockerfile .`
3) change some dependency in the toml file
4) run `poetry lock`
5) rerun `DOCKER_BUILDKIT=1 docker build --progress=plain -t airflow-test -f Dockerfile .`
6) if poetry install is installing only the changed dependency it worked
FROM python:3.4
WORKDIR /usr/src/app

# install supervisord
RUN apt-get update && apt-get install -y supervisor

# copy requirements and install (so that changes to files do not mean rebuild cannot be cached)
COPY requirements.txt /usr/src/app
RUN pip install -r requirements.txt

# copy all files into the container
COPY . /usr/src/app

# needs to be set else Celery gives an error (because docker runs commands inside container as root)
ENV C_FORCE_ROOT=1

# run supervisord
CMD ["/usr/bin/supervisord"]

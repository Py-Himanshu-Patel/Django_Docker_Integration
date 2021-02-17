# Base Image whice we use to make docker image
FROM python:3.9

# make a dir to keep all code of project and mark it as working dir
RUN mkdir /app
WORKDIR /app

# add current directory to working directory
ADD . /app/

# set environment variable and get them using os.environ.get()
ENV PYTHONUNBUFFERED=1
ENV DEBUG=False
ENV PORT=8000 

# copy requirements.txt to docker image file 
COPY requirements.txt /app/requirements.txt
# add command to run requirements.txt
RUN pip install -r requirements.txt

# copy remaining data from current dir to working dir
COPY . /app/

# to make request on gunicorn
EXPOSE 8000
CMD gunicorn first.wsgi:application --bind 0.0.0.0:$PORT

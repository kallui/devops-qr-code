FROM python:3.9

# set wd in container
WORKDIR /usr/src/app

# install dependencies
COPY requirements.txt ./

RUN pip install --no-cache-dir -r requirements.txt

# copy everything to the container
COPY . .

#run app
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "80"]
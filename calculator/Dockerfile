FROM python:3.6-slim
MAINTAINER viseth89@gmail.com
COPY . /calculator
WORKDIR /calculator
RUN pip install --no-cache-dir -r requirements.txt
RUN ["pytest", "-v", "--junitxml=reports/result.xml"]
CMD tail -f /dev/null
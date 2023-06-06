FROM python:latest

#create work dir
ADD app /app
WORKDIR /app

RUN pip3 install -r requirements.txt

#Run the script
ENTRYPOINT ["python","-u","event_watcher.py"]

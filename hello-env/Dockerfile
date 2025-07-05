FROM ubuntu:20.04

ENV user_name="prudvi"
ENV env_mode="development"

WORKDIR /app

COPY app.sh .

RUN apt-get update && apt-get install -y bash

CMD ["bash", "app.sh"]

FROM python:3.13-slim-bookworm
WORKDIR /code
ENV TZ=Asia/Taipei
RUN apt-get update && apt-get upgrade -y && apt-get clean
COPY ./requirements.txt /code/requirements.txt
RUN pip install --no-cache-dir -r requirements.txt
COPY ./src /code/src
COPY entrypoint.sh /code/entrypoint.sh
RUN chmod +x ./entrypoint.sh
ENTRYPOINT ["./entrypoint.sh"]
FROM python:3.8.10-slim
ENV WERKZEUG_DEBUG_PIN=REDACTED
ADD . /app
WORKDIR /app
RUN apt update \
    && apt install -y firefox-esr \
    && pip install -r requirements.txt
CMD flask --debug run -h 0.0.0.0 -p 5000

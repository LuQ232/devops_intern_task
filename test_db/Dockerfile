FROM alpine:3.14

COPY . .

RUN apk update &&\
    apk add git

RUN git clone https://github.com/datacharmer/test_db.git

CMD ["sleep", "infinity"]
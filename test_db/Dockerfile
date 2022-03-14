FROM alpine:3.14 AS basic_stage
COPY . .

RUN apk update &&\
    apk add git

RUN git clone https://github.com/datacharmer/test_db.git &&\
    mkdir db_dump &&\
    cp test_db/*.dump /db_dump &&\
    cp test_db/employees.sql /db_dump &&\
    cp test_db/show_elapsed.sql /db_dump



FROM mysql:8.0-oracle
COPY --from=basic_stage ./db_dump ./db_dump
WORKDIR /docker-entrypoint-initdb.d
RUN ln -fsn /db_dump/* /docker-entrypoint-initdb.d
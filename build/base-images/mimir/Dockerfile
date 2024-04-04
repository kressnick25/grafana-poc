FROM alpine:latest


RUN mkdir /mimir
WORKDIR /mimir

COPY ./src ./

ENTRYPOINT [ "./mimir-linux-amd64" ]
CMD ["--config.file=./config.yaml"]
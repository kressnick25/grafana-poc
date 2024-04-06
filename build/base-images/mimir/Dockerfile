FROM registry.access.redhat.com/ubi8/ubi:latest

ARG MIMIR_VERSION=2.12.0

LABEL name="ubi8/mimir-mono" \
      version="$MIMIR_VERSION" \
      description="Grafana Mimir in monolithic mode" \
      com.redhat.component="mimir-container" \
      io.k8s.display-name="Mimir" \
      io.openshift.expose-services="9009:mimir" \
      io.openshift.tags="grafana,monitoring"

RUN dnf upgrade -y && \
    curl -LJO https://github.com/grafana/mimir/releases/download/mimir-${MIMIR_VERSION}/mimir-${MIMIR_VERSION}_amd64.rpm && \
    dnf install -y ./mimir-${MIMIR_VERSION}_amd64.rpm && \
    dnf clean all

RUN rm /etc/mimir/*
# TODO this will need to be moved to a ConfigMap
COPY ./config.yaml /etc/mimir/config.yaml

EXPOSE 9009
ENTRYPOINT ["/usr/local/bin/mimir"]
CMD ["--config.file=/etc/mimir/config.yaml"]

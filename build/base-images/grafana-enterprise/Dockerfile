FROM registry.access.redhat.com/ubi8/ubi:latest

ARG GRAFANA_VERSION=10.4.1

LABEL name="ubi8/grafana-enterprise" \
      version="$GRAFANA_VERSION" \
      com.redhat.component="grafana-container" \
      io.k8s.display-name="Grafana" \
      io.openshift.expose-services="3000:grafana" \
      io.openshift.tags="grafana,monitoring,dashboard"

RUN dnf upgrade -y && \
    curl -O https://dl.grafana.com/enterprise/release/grafana-enterprise-${GRAFANA_VERSION}-1.x86_64.rpm && \
    dnf install -y grafana-enterprise-${GRAFANA_VERSION}-1.x86_64.rpm && \
    dnf clean all

EXPOSE 3000

ENV GF_PATHS_CONFIG /etc/grafana

WORKDIR /usr/share/grafana
CMD ["/usr/share/grafana/bin/grafana-server", "--homepath=/usr/share/grafana"]

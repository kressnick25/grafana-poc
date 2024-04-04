FROM registry.access.redhat.com/ubi9/ubi:latest

RUN echo "Test output"

RUN dnf update -y

RUN curl -O https://dl.grafana.com/enterprise/release/grafana-enterprise-10.4.1-1.x86_64.rpm && \
    dnf install -y grafana-enterprise-10.4.1-1.x86_64.rpm 

EXPOSE 3000

ENV GF_PATHS_CONFIG /etc/grafana

CMD ["/usr/share/grafana/bin/grafana-server", "--homepath=/usr/share/grafana"]

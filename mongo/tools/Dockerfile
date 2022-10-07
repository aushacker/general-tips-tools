FROM registry.access.redhat.com/ubi8-minimal:latest

RUN microdnf --setopt=tsflags=nodocs install -y tar gzip && \
    curl -o /tmp/mongo-tools.tgz https://fastdl.mongodb.org/tools/db/mongodb-database-tools-rhel80-x86_64-100.6.0.tgz && \
    tar -xf /tmp/mongo-tools.tgz -C /tmp/ && \
    mv /tmp/mongo*/bin/* /usr/local/bin/ && \
#    curl -o /tmp/mongosh.rpm https://downloads.mongodb.com/compass/mongodb-mongosh-1.6.0.x86_64.rpm?_ga=2.128587656.507764704.1665035984-1916017753.1665035984 && \
#    microdnf install -y /tmp/mongosh.rpm && \
    microdnf clean all

CMD ["sleep", "infinity"]

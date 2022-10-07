FROM registry.access.redhat.com/ubi8-minimal:latest

RUN curl -o /tmp/mongo-tools.tgz https://fastdl.mongodb.org/tools/db/mongodb-database-tools-rhel80-x86_64-100.6.0.tgz && \
    tar -xf /tmp/mongo-tools.tgz -C /tmp/mongo-tools/

ENTRYPOINT["sleep", "3600"]

FROM registry.access.redhat.com/ubi8:latest

RUN curl -o /tmp/mongo-tools.tgz https://fastdl.mongodb.org/tools/db/mongodb-database-tools-rhel80-x86_64-100.6.0.tgz && \
    tar -xf /tmp/mongo-tools.tgz -C /tmp/ && \
    mv /tmp/mongo*/bin/* /usr/local/bin/ && \
    curl -o /tmp/mongosh.rpm https://downloads.mongodb.com/compass/mongodb-mongosh-1.6.0.x86_64.rpm?_ga=2.128587656.507764704.1665035984-1916017753.1665035984 && \
    rpm -i /tmp/mongosh.rpm

CMD ["sleep", "infinity"]

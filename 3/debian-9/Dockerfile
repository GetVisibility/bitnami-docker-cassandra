FROM bitnami/minideb-extras:stretch-r237
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    HOME="/"

# Install required system packages and dependencies
RUN install_packages libbz2-1.0 libc6 libgcc1 libjemalloc1 libncurses5 libreadline7 libsqlite3-0 libssl1.1 libtinfo5 zlib1g
RUN bitnami-pkg install python-2.7.15-20 --checksum 77c68cc5c463e53143bb7b6e6d322d5127d9cf4bd988b1aa217db2640e86e5fd
RUN bitnami-pkg install java-1.8.191-20 --checksum e193fab6c3c4de4d30f81a09d3b33978baa31761aaa330e39ce5ae8753db4133
RUN bitnami-pkg unpack cassandra-3.11.3-24 --checksum aa5053ef4c3d8a739d4a956c4743c246e8382505af33752d4adb3229430dd667
RUN mkdir -p /docker-entrypoint-initdb.d /opt/bitnami/cassandra/conf/
RUN chmod -R g+rwX /opt/bitnami/cassandra/conf/

COPY rootfs /
ENV BITNAMI_APP_NAME="cassandra" \
    BITNAMI_IMAGE_VERSION="3.11.3-debian-9-r140" \
    CASSANDRA_CLIENT_ENCRYPTION="false" \
    CASSANDRA_CLUSTER_NAME="My Cluster" \
    CASSANDRA_CQL_PORT_NUMBER="9042" \
    CASSANDRA_DATACENTER="dc1" \
    CASSANDRA_ENABLE_REMOTE_CONNECTIONS="true" \
    CASSANDRA_ENABLE_RPC="true" \
    CASSANDRA_ENDPOINT_SNITCH="SimpleSnitch" \
    CASSANDRA_HOST="" \
    CASSANDRA_INTERNODE_ENCRYPTION="none" \
    CASSANDRA_JMX_PORT_NUMBER="7199" \
    CASSANDRA_KEYSTORE_PASSWORD="cassandra" \
    CASSANDRA_NUM_TOKENS="256" \
    CASSANDRA_PASSWORD="cassandra" \
    CASSANDRA_PASSWORD_SEEDER="no" \
    CASSANDRA_RACK="rack1" \
    CASSANDRA_SEEDS="" \
    CASSANDRA_STARTUP_CQL="" \
    CASSANDRA_TRANSPORT_PORT_NUMBER="7000" \
    CASSANDRA_TRUSTSTORE_PASSWORD="cassandra" \
    CASSANDRA_USER="cassandra" \
    NAMI_PREFIX="/.nami" \
    PATH="/opt/bitnami/python/bin:/opt/bitnami/java/bin:/opt/bitnami/cassandra/bin:$PATH"

EXPOSE 9042 7000

USER 1001
ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "/run.sh" ]

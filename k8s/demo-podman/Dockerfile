FROM registry.access.redhat.com/ubi8/podman:latest 

ENV _BUILDAH_STARTED_IN_USERNS="" \
    BUILDAH_ISOLATION=chroot \
    STORAGE_DRIVER=vfs \
    HOME=/home/podman

USER root

# Setup for azure and tools
RUN dnf update -y && \
    dnf install -y --setopt=tsflags=nodocs git skopeo podman-docker --exclude container-selinux && \
    dnf clean all && \
    chown -R podman:0 /home/podman && \
    chmod -R 775 /home/podman && \
    chmod -R 775 /etc/alternatives && \
    chmod -R 775 /var/lib/alternatives && \
    chmod -R 775 /usr/bin && \
    chmod 775 /usr/share/man/man1 && \
    mkdir -p /var/lib/origin && \
    chmod 775 /var/lib/origin && \
    chmod u-s /usr/bin/newuidmap && \
    chmod u-s /usr/bin/newgidmap && \
    rm -f /var/logs/*

USER 1000

FROM centos/php-70-centos7

USER root

ENV PATH=$PATH:/opt/rh/rh-nodejs4/root/usr/bin \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/rh/rh-nodejs4/root/usr/lib64

RUN INSTALL_PKGS="rh-nodejs4-npm" && \
    yum install -y --setopt=tsflags=nodocs --enablerepo=centosplus $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y && \
    npm install -g bower grunt gulp-cli phantomjs-prebuilt@2.1.14

USER 1001

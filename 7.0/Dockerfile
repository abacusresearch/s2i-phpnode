FROM centos/php-70-centos7

USER root

ENV PATH=$PATH:/opt/rh/rh-nodejs4/root/usr/bin \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/rh/rh-nodejs4/root/usr/lib64

RUN INSTALL_PKGS="rh-nodejs4-npm" && \
    yum install -y --setopt=tsflags=nodocs --enablerepo=centosplus $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y && \
    npm install -g bower grunt gulp-cli phantomjs-prebuilt@2.1.14

# Each language image can have 'contrib' a directory with extra files needed to
# run and build the applications.
COPY ./contrib/ /opt/app-root

# In order to drop the root user, we have to make some directories world
# writeable as OpenShift default security model is to run the container under
# random UID.
RUN sed -i -f /opt/app-root/etc/httpdconf.sed /opt/rh/httpd24/root/etc/httpd/conf/httpd.conf && \
    chmod -R ug+rwx /opt/app-root

USER 1001

FROM fedora:latest

RUN dnf -y install openssh-server rsync

# setup openssh
RUN sed -i "s/#PasswordAuthentication yes/PasswordAuthentication no/" /etc/ssh/sshd_config
RUN chmod 775 /etc/ssh /home # keep writable for openshift user group (root)
RUN chmod 660 /etc/ssh/sshd_config
RUN mkdir /var/run/sshd
RUN rm -f /var/run/nologin

EXPOSE 22
CMD exec /usr/sbin/sshd -D

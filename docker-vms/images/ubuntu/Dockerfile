FROM ubuntu:20.04
RUN apt-get update && apt-get install -y openssh-server vim sudo bash
RUN mkdir /var/run/sshd
RUN echo 'root:PASSWORD' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
RUN useradd -m mahsan
RUN echo "mahsan:test" | chpasswd
RUN echo "mahsan  ALL=(ALL)  NOPASSWD: ALL" >> /etc/sudoers
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

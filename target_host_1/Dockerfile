FROM python:3.8.5

RUN apt-get update && apt-get -y install --no-install-recommends openssh-server sudo \
&& rm -rf /var/lib/apt/lists/*
RUN mkdir /root/.ssh
RUN sed -ri 's/^#PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config \
&& /etc/init.d/ssh start \
&& sed -ri 's/#PermitEmptyPasswords no/PermitEmptyPasswords no/g' /etc/ssh/sshd_config \
&& sed -ri 's/#PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config \
&& sed -ri 's/# ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
EXPOSE 22

CMD /usr/sbin/sshd -D

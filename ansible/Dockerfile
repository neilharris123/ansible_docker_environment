FROM alpine:3.12.0

Maintainer Neil Harris       https://github.com/neilharris123

RUN apk update && \
apk add --no-cache ansible bash openssh-client && rm -rf /var/cache/apk/*
RUN ssh-keygen -q -t rsa -N '' -f /root/.ssh/id_rsa && cp /root/.ssh/id_rsa.pub /mnt/authorized_keys
RUN mkdir /etc/ansible
WORKDIR /etc/ansible
COPY ansible.cfg /etc/ansible/
ADD environments /etc/ansible/environments

CMD bash -c '/bin/cp ~/.ssh/id_rsa.pub /mnt/authorized_keys && /usr/bin/tail -f /dev/null'

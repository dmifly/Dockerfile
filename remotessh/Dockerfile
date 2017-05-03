FROM alpine

RUN apk --no-cache add openssh \
	&& sed -i s/#PermitRootLogin.*/PermitRootLogin\ yes/ /etc/ssh/sshd_config \
	&& echo "GatewayPorts yes" >> /etc/ssh/sshd_config \
 	&& rm -rf /var/cache/apk/* \
	&& ssh-keygen -A

EXPOSE 22 4445 4446 4447 4448
ENTRYPOINT   echo "root:$PASSWORD" | chpasswd ; /usr/sbin/sshd -D -e "$@"



FROM ubuntu:22.04

# Evitar preguntas al instalar paquetes
ENV DEBIAN_FRONTEND=noninteractive

# Actualizamos e instalamos openssh-server y sudo
RUN apt update && apt install -y openssh-server sudo && \
    mkdir /var/run/sshd

# Creamos usuario ansible con password ansible
RUN useradd -m ansible && echo "ansible:ansible" | chpasswd

# Dar sudo sin password al usuario ansible
RUN echo "ansible ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Habilitar SSH
EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]

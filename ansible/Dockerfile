FROM ubuntu:latest

RUN apt-get update -y
RUN apt-get install -y ssh
RUN apt-get install -y python3
RUN apt-get install -y python3-pip

RUN pip install pip --upgrade
RUN pip install ansible

RUN ansible-galaxy install xanmanning.k3s

WORKDIR /work

COPY ssh /root/.ssh
RUN chmod 600 /root/.ssh/id_rsa

COPY . /work

CMD ansible-playbook -i hosts --ask-become-pass playbook.yaml
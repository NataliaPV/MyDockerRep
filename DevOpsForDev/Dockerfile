
# # How to execute docker run -it devdockerdevelop bash
#FROM ubuntu:18.04 as system

FROM dorowu/ubuntu-desktop-lxde-vnc
RUN apt update
RUN apt install -y git
RUN apt install -y python3.5
RUN apt-get install -y openjdk-8-jdk
RUN apt install -y curl
RUN apt install -y wget
RUN curl -O https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh
RUN apt update -y
RUN apt-get upgrade -y python3
RUN apt install -y maven
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:notepadqq-team/notepadqq
RUN apt-get update
RUN apt install -y nano
RUN git clone https://github.com/NataliaPV/MyDockerRep.git /gitclone
WORKDIR /gitclone/DevOpsForDev/
RUN cp scala.nanorc java.nanorc sql.nanorc /usr/share/nano/
RUN cp nanorc /etc/
RUN git clone https://github.com/NataliaPV/ScalaMainRep.git /gitclone/ProjectCore/
WORKDIR /gitclone/ProjectCore/
RUN mkdir /gitclone/LocalProjectCore/
RUN cp -r lib pom.xml src /gitclone/LocalProjectCore/
#RUN cp -r /gitclone/ProjectCore/crongitpush.sh  /gitclone/LocalProjectCore/crongitpush.sh
WORKDIR /gitclone/LocalProjectCore/
RUN wget www.scala-lang.org/files/archive/scala-2.11.8.deb
RUN dpkg -i scala-2.11.8.deb
RUN rm scala-2.11.8.deb
WORKDIR /gitclone/ProjectCore/
RUN crontab -l */5 * * * * ~/bash crongitpush.sh

# mvn clean compile - только компиляция
# mvn clean compile assembly:single - сборка толстого джарника

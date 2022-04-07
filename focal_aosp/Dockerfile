FROM ubuntu:focal
#### for China 
RUN rm /etc/apt/sources.list
RUN echo "deb http://mirrors.bfsu.edu.cn/ubuntu/ focal main restricted universe multiverse" | tee /etc/apt/sources.list
RUN echo "deb http://mirrors.bfsu.edu.cn/ubuntu/ focal-updates main restricted universe multiverse" >> /etc/apt/sources.list
RUN echo "deb http://mirrors.bfsu.edu.cn/ubuntu/ focal-backports main restricted universe multiverse" >> /etc/apt/sources.list
RUN echo "deb http://mirrors.bfsu.edu.cn/ubuntu/ focal-security main restricted universe multiverse" >> /etc/apt/sources.list
#### for Chine end
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update -y && apt-get install -y software-properties-common
RUN add-apt-repository -y ppa:deadsnakes/ppa
RUN apt-get update -y && apt-get install -y python3.8
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 150
RUN apt-get install -y python3-pip && pip install pycrypto
RUN apt-get update -y && apt-get install -y openjdk-8-jdk python git-core gnupg flex bison gperf build-essential \
zip curl gawk liblz4-tool zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 \
lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache \
libgl1-mesa-dev libxml2-utils xsltproc unzip mtools u-boot-tools \
htop iotop sysstat iftop pigz bc device-tree-compiler lunzip \
dosfstools vim-common parted udev libssl-dev  sudo rsync python3-pyelftools cpio
#### For China
RUN curl https://mirrors.bfsu.edu.cn/git/git-repo > /usr/local/bin/repo && \
chmod +x /usr/local/bin/repo && \
which repo
ENV REPO_URL='https://mirrors.bfsu.edu.cn/git/git-repo/'
#### For China End
RUN pip install pycrypto
ENV USER=android11-docker
ARG USER_ID=1000
ARG GROUP_ID=1000
RUN groupadd -g ${GROUP_ID} jenkins-docker && useradd -m -g jenkins-docker -u ${USER_ID} android11-docker
USER android11-docker


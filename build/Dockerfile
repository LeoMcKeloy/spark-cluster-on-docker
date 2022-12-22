FROM andreper/spark-master:3.0.0

RUN apt update -y && \
    apt-get install -y openssh-server && \
    mkdir /root/.ssh && \
    touch /root/.ssh/authorized_keys && \
    apt-get clean;

COPY ./id_rsa.pub /root/.ssh/
COPY ./sshd_config /etc/ssh/sshd_config

RUN cat /root/.ssh/id_rsa.pub > /root/.ssh/authorized_keys

EXPOSE 22

CMD service ssh start && bin/spark-class org.apache.spark.deploy.master.Master >> logs/spark-master.out
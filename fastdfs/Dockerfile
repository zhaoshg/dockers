FROM debian:jessie-slim
MAINTAINER Zhao Shuguang "zhaoshg@aliyun.com"

ADD fastdfs-5.10.tar.gz /home
ADD libfastcommon-master.tar.gz /home
ADD sources.list /etc/apt/
ADD startfdfs.sh /etc/init.d/

RUN apt-get update && \
	apt-get install -y gcc && \
	apt-get install -y make && \
	cd /home/libfastcommon-master && \
	./make.sh && \
	./make.sh install && \
	ln -s /usr/lib64/libfastcommon.so /usr/local/lib/libfastcommon.so && \
	ln -s /usr/lib64/libfdfsclient.so /usr/local/lib/libfdfsclient.so && \
	cd /home/fastdfs-5.10 && \
	./make.sh && \
	./make.sh install && \
	ln -s /usr/bin/fdfs_trackerd /usr/local/bin && \
	ln -s /usr/bin/stop.sh /usr/local/bin && \
	ln -s /usr/bin/restart.sh /usr/local/bin && \
	ln -s /usr/bin/fdfs_storaged /usr/local/bin && \
	sed -i '13 d' /etc/init.d/fdfs_trackerd && \
	sed -i '13 d' /etc/init.d/fdfs_storaged && \
	apt-get purge -y gcc make && \
	apt-get autoremove -y && \
	apt-get clean && \
	dpkg -l |grep ^rc|awk '{print $2}' | xargs dpkg -P && \
	mkdir /fastdfs && \
	cd /home && \
	rm -rf /home/fastdfs-5.10 /home/libfastcommon-master && \
	chmod +x /etc/init.d/startfdfs.sh

ADD conf.tar.gz /etc/fdfs/

EXPOSE 22122

VOLUME /fastdfs
CMD /etc/init.d/startfdfs.sh
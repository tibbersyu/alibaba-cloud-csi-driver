FROM registry.cn-hangzhou.aliyuncs.com/plugins/centos:7.6.1810
LABEL maintainers="Alibaba Cloud Authors"
LABEL description="Alibaba Cloud CSI Plugin"

RUN yum install -y ca-certificates file tzdata nfs-utils xfsprogs e4fsprogs

ARG ossfsVer=1.80.6.ack.1
RUN curl http://ack-csiplugin.oss-cn-hangzhou.aliyuncs.com/ossfs/ossfs_1.80.6.ack.1-b42b3a8_centos7.0_x86_64.rpm -o /root/ossfs_${ossfsVer}_centos7.0_x86_64.rpm
COPY nsenter /nsenter
COPY entrypoint.sh /entrypoint.sh
COPY csiplugin-connector /bin/csiplugin-connector
COPY csiplugin-connector.service /bin/csiplugin-connector.service
COPY plugin.csi.alibabacloud.com /bin/plugin.csi.alibabacloud.com
RUN chmod +x /bin/plugin.csi.alibabacloud.com && chmod +x /entrypoint.sh && chmod +x /bin/csiplugin-connector && chmod +x /bin/csiplugin-connector.service

ENTRYPOINT ["/entrypoint.sh"]

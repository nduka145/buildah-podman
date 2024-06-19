FROM enterpriseartifactory.bkfs.com:5000/rhel8/python-39
WORKDIR /opt
COPY requirements.txt requirements.txt
RUN rm -f /etc/pip.conf
COPY pip.conf /etc/pip.conf
RUN pip3 install -r requirements.txt
COPY collections collections
COPY ss.yml ss.yml
COPY inv inv
USER root
COPY ca.crt /etc/pki/ca-trust/source/anchors/
RUN chown -R default:root ./*
RUN update-ca-trust
ENV REQUESTS_CA_BUNDLE='/etc/pki/ca-trust/source/anchors/ca.crt'
USER default

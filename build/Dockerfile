FROM jbenet/go-ipfs:latest as ipfs

FROM node:alpine

RUN apk --no-cache add ca-certificates wget git python build-base
RUN wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://raw.githubusercontent.com/sgerrand/alpine-pkg-glibc/master/sgerrand.rsa.pub
RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.27-r0/glibc-2.27-r0.apk
RUN apk add glibc-2.27-r0.apk

# Create the fs-repo directory and switch to a non-privileged user.
ENV IPFS_PATH /data/ipfs
RUN mkdir -p $IPFS_PATH \
  && adduser -D -h $IPFS_PATH -G users ipfs \
  && chown ipfs:users $IPFS_PATH

COPY --from=ipfs /usr/local/bin/ipfs /usr/local/bin/
COPY --from=ipfs /sbin/su-exec /sbin/su-exec
COPY --from=ipfs /sbin/tini /sbin/tini
COPY --from=ipfs /etc/ssl/certs /etc/ssl/certs

COPY start_ipfs /usr/local/bin/start_ipfs
COPY entrypoint /usr/local/bin/entrypoint

RUN git clone https://github.com/ipfsconsortium/IPFSConsortiumProxy.git
RUN cd IPFSConsortiumProxy && npm install && npm link

ENV IPFSAPIHOST=localhost
ENV IPFSAPIPORT=5001
ENV WEB3HOSTWS="wss://mainnet.infura.io/ws"
ENV CONTRACTADDRESS="0x7433c7c768be4025ab791fb7b2942c3d9e309f3e"
ENV STARTBLOCK=4090116
ENV IPFS_ENABLE=true

ENTRYPOINT [ "entrypoint" ]

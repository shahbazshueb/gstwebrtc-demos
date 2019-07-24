FROM ubuntu:19.04

# RUN apt-get install -y libjson-glib-dev
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y libgstreamer-plugins-bad1.0-dev libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools gstreamer1.0-nice gir1.2-nice-0.1 libnice-dev  
RUN apt-get install -y libjson-glib-dev libsoup2.4-dev
# RUN apk update
# RUN apk add json-glib-dev libsoup-dev

WORKDIR /opt/
COPY . /opt/

RUN make

CMD echo "Waiting a few seconds for you to open the browser at localhost:8080" \
    && sleep 10 \
    && ./webrtc-sendrecv \
    --peer-id=1 \
    --server=ws://signalling:8443 \
    --disable-ssl


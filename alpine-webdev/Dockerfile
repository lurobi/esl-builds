FROM alpine:latest
LABEL maintainer="robison@arlut.utexas.edu"
LABEL version="1.0"

COPY ./vscode_server.sh /tmp/vscode_server.sh
RUN /bin/sh /tmp/vscode_server.sh

RUN apk add --no-cache python3 py3-pip npm git

RUN pip3 install wheel flask

# It is necessary to specify WORKDIR for non-global npm installs.

RUN npm install -g react create-react-app react-dom cra-template && rm -rf ~/.npm

WORKDIR /usr/app
RUN create-react-app /usr/app && rm -rf ~/.npm




FROM nginx:1.19.6-alpine

ENV LANG ja_jp.utf8
ENV ENTRYKIT_VERSION 0.4.0

RUN wget https://github.com/progrium/entrykit/releases/download/v${ENTRYKIT_VERSION}/entrykit_0.4.0_Linux_x86_64.tgz \
    && tar -xzvf entrykit_${ENTRYKIT_VERSION}_Linux_x86_64.tgz \
    && rm entrykit_${ENTRYKIT_VERSION}_Linux_x86_64.tgz \
    && mv entrykit /usr/local/bin/ \
    && entrykit --symlink

COPY ./nginx.conf.tmpl /etc/nginx/nginx.conf.tmpl

ENTRYPOINT [ "render", "/etc/nginx/nginx.conf", "--" ]

CMD [ "nginx", "-g", "daemon off;" ]
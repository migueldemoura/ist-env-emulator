FROM nginx

ARG SERVER_NAME

RUN usermod -u 1000 www-data

COPY nginx.conf /etc/nginx/
COPY ist-env-emulator.conf /ist-env-emulator.conf
RUN envsubst '${SERVER_NAME}' < /ist-env-emulator.conf > /etc/nginx/conf.d/ist-env-emulator.conf && rm /ist-env-emulator.conf
RUN rm /etc/nginx/conf.d/default.conf

COPY tls/ist-env-emulator.pem /etc/nginx/ssl/ist-env-emulator.pem
COPY tls/ist-env-emulator.key /etc/nginx/ssl/ist-env-emulator.key

CMD ["nginx"]

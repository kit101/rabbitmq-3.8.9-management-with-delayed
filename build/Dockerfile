FROM mwendler/wget as plugin-downloader
WORKDIR /plugins
RUN wget --no-check-certificate 'https://github-releases.githubusercontent.com/32327910/fb8cf200-1884-11eb-8a3a-86e8864bf669?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20210811%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20210811T082721Z&X-Amz-Expires=300&X-Amz-Signature=b48604f4c20b9e223e5935cfe1bb96c749b6c285b7609a54ff7c1f66c268e082&X-Amz-SignedHeaders=host&actor_id=23008405&key_id=0&repo_id=32327910&response-content-disposition=attachment%3B%20filename%3Drabbitmq_delayed_message_exchange-3.8.9-0199d11c.ez&response-content-type=application%2Foctet-stream' -O rabbitmq_delayed_message_exchange-3.8.9-0199d11c.ez

FROM rabbitmq:3.8.9-management
COPY --from=plugin-downloader /plugins/rabbitmq_delayed_message_exchange-3.8.9-0199d11c.ez /plugins
RUN rabbitmq-plugins list
RUN rabbitmq-plugins enable rabbitmq_delayed_message_exchange
CMD ["rabbitmq-server"]
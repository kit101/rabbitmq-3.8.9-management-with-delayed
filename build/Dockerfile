# declare rabbitmq tag
FROM rabbitmq:3.8.9-management
# copy all custom plugins to image:/plugins
COPY plugins/* /plugins
RUN rabbitmq-plugins list

# enable plugins begin =====
RUN rabbitmq-plugins enable rabbitmq_delayed_message_exchange
# enable other plugins in here
# enable plugins end =====

RUN rabbitmq-plugins list

CMD ["rabbitmq-server"]
FROM jeremycurny/php-magento2:7.1-fpm-stretch

MAINTAINER "Jeremy CURNY" <jeremy.curny.pro@gmail.com>

ARG DEBIAN_FRONTEND=noninteractive

ENV MAGENTO_ARTIFACT_NAME m2-ce230.tar.gz
ENV MAGENTO_PROJECT_VERSION 2.3.0

RUN \
  composer global config --auth http-basic.repo.magento.com $MAGENTO_PUB_KEY $MAGENTO_PRI_KEY \
  && composer create-project --repository-url=https://repo.magento.com/ $MAGENTO_PROJECT=$MAGENTO_PROJECT_VERSION $TMP_DECK \
  && composer clear-cache \
  && tar -czf $ARTIFACT_PATH/$MAGENTO_ARTIFACT_NAME -C $TMP_DECK . \
  && rm -rf $TMP_DECK && mkdir -p $TMP_DECK

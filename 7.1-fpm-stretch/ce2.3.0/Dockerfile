FROM jeremycurny/php-magento2:7.1-fpm-stretch

MAINTAINER "Jeremy CURNY" <jeremy.curny.pro@gmail.com>

ARG DEBIAN_FRONTEND=noninteractive

ENV MAGENTO_PUB_KEY 6c7c3956d991c6459bcbf6d0d977514f
ENV MAGENTO_PRI_KEY 2319f30adac6169a5c30ad2cb564d177

ENV MAGENTO_PROJECT_VERSION 2.3.0

RUN \
  rm -rf $TMP_DECK && mkdir -p $TMP_DECK \
  && composer global config --auth http-basic.repo.magento.com $MAGENTO_PUB_KEY $MAGENTO_PRI_KEY \
  && composer create-project --repository-url=https://repo.magento.com/ $MAGENTO_COMMUNITY_PROJECT=$MAGENTO_PROJECT_VERSION $TMP_DECK \
  && composer clear-cache \
  && tar -czf $ARTIFACT_PATH/$MAGENTO_COMMUNITY_PROJECT/$MAGENTO_PROJECT_VERSION.tar.gz -C $TMP_DECK . \
  && rm -rf $TMP_DECK && mkdir -p $TMP_DECK

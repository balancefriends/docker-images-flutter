FROM ghcr.io/amondnet/android-sdk:30

USER root

ARG flutter_version=stable

ENV FLUTTER_HOME=${HOME}/sdks/flutter \
    FLUTTER_VERSION=$flutter_version
ENV FLUTTER_ROOT=$FLUTTER_HOME

ENV PATH ${PATH}:${FLUTTER_HOME}/bin:${FLUTTER_HOME}/bin/cache/dart-sdk/bin:${HOME}/.pub-cache/bin

RUN git clone --depth 1 --branch ${FLUTTER_VERSION} https://github.com/flutter/flutter.git ${FLUTTER_HOME}

RUN yes | flutter doctor --android-licenses \
    && flutter doctor \
    && flutter precache \
    && chown -R root:root ${FLUTTER_HOME}
    

RUN dart pub global activate melos \
    && dart pub global activate coverage \
    && dart pub global activate full_coverage \
    && dart pub global activate remove_from_coverage \
    && dart pub global activate grinder

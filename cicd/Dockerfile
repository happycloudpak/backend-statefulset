FROM openjdk:8-jdk-alpine

ENV ARTIFACTORY_FILE backend-statefulset.jar
ENV ARTIFACTORY_HOME /usr/artifactory

# Add a docker user, make work dir
RUN adduser --disabled-password --gecos "" docker && echo "docker ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers && mkdir -p ${ARTIFACTORY_HOME} && chown docker:docker ${ARTIFACTORY_HOME}

WORKDIR ${ARTIFACTORY_HOME}

# Copy your jar to the container
COPY ./target/${ARTIFACTORY_FILE} ${ARTIFACTORY_HOME}

# Launch the artifactory as docker user
ENTRYPOINT [ "sh", "-c" ]
USER docker
CMD [ "exec java -jar ${ARTIFACTORY_FILE}" ]
FROM wayoyo/bootstrap:0.1

ENV APPLICATION_USER=application \
    APPLICATION_GROUP=application \
    APPLICATION_PATH=/app \
    APPLICATION_UID=1000 \
    APPLICATION_GID=1000

RUN set -x \
    # Install Services
    && apt-install \
        git \
        vim \
        less \
    && docker-image-cleanup \
    && cli-create-user

USER ${APPLICATION_USER}
SHELL ["/bin/bash", "-c"]

RUN set -x \
    && echo -e "\n\n## Custom commands" >> ~/.bashrc \
    && echo -e "macchina --show host,kernel,memory,processor,uptime" >> ~/.bashrc \
    && echo -e 'eval "$(oh-my-posh init bash --config /usr/share/oh-my-posh.theme.json)"' >> ~/.bashrc

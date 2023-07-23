# Molecule managed

{% if item.registry is defined %}
FROM {{ item.registry.url | lower }}/{{ item.image | lower }}
{% else %}
FROM {{ item.image | lower }}
{% endif %}

{% if item.env is defined %}
{% for var, value in item.env.items() %}
{% if value %}
ENV {{ var }} {{ value }}
{% endif %}
{% endfor %}
{% endif %}

ARG RELEASE
ARG LAUNCHPAD_BUILD_ARCH
ARG DEBIAN_FRONTEND=noninteractive
ARG container=docker

RUN apt-get update && apt-get install -y --no-install-recommends \
                apt-utils \
                curl \
                debian-archive-keyring \
                gpg-agent \
                gnupg \
                nano \
                python3 \
                software-properties-common \
                rsyslog \
                sudo \
                && apt-get clean \
                && rm -Rf /var/lib/apt/lists/* \
                && rm -Rf /usr/share/doc \
                && rm -Rf /usr/share/man

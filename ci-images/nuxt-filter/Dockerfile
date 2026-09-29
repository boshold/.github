FROM mcr.microsoft.com/playwright:v1.63.0-noble@sha256:eff16c30e6f3f4af0a03fa4b706120d5e9b0891c344a27d64559aff5900a4a27
LABEL org.opencontainers.image.source="https://github.com/boshold/.github"

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update -qq \
  && apt-get install -y --no-install-recommends ca-certificates curl gnupg libicu-dev postgresql-common \
  && install -d -m 0755 /usr/share/postgresql-common/pgdg \
  && curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc \
  && echo 'deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt noble-pgdg main' > /etc/apt/sources.list.d/pgdg.list \
  && apt-get update -qq \
  && apt-get install -y --no-install-recommends postgresql-18 postgresql-client-18 \
  && rm -rf /var/lib/apt/lists/*

ENV COREPACK_HOME=/opt/corepack
ENV COREPACK_DEFAULT_TO_LATEST=0
RUN corepack enable \
  && corepack install -g pnpm@11.24.0 \
  && chmod -R a+rX /opt/corepack \
  && mkdir -p /workspace \
  && chown pwuser:pwuser /workspace \
  && runuser -u pwuser -- bash -lc 'test "$(pnpm --version)" = 11.24.0'
ENV PATH="/usr/lib/postgresql/18/bin:${PATH}"
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright
WORKDIR /workspace
USER pwuser

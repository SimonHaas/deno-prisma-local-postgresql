FROM mcr.microsoft.com/devcontainers/javascript-node

RUN curl -s https://packages.stripe.dev/api/security/keypair/stripe-cli-gpg/public | gpg --dearmor | tee /usr/share/keyrings/stripe.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/stripe.gpg] https://packages.stripe.dev/stripe-cli-debian-local stable main" | tee -a /etc/apt/sources.list.d/stripe.list && \
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    stripe \
    mariadb-client \
    postgresql-client \
    iputils-ping \
    direnv && \
    rm -rf /var/lib/apt/lists/* && \
    curl -s https://gist.githubusercontent.com/LukeChannings/09d53f5c364391042186518c8598b85e/raw/ac8cd8c675b985edd4b3e16df63ffef14d1f0e24/deno_install.sh | sh  && \
    export DENO_INSTALL=/root/.deno && \
    export PATH=$DENO_INSTALL/bin:$PATH && \
    echo "export DENO_INSTALL=/root/.deno" >> ~/.bashrc && \
    echo "export PATH=$DENO_INSTALL/bin:$PATH" >> ~/.bashrc && \
    echo '#!/bin/bash' >> /usr/bin/supabase && \
    echo 'npx supabase "$@"' >> /usr/bin/supabase && \
    chmod +x /usr/bin/supabase && \
    npx --yes supabase && \
    npm i -g wrangler && \
    echo 'eval "$(direnv hook bash)"' >> ~/.bashrc && \
    echo 'eval "$(direnv hook bash)"' >> ~/.bash_profile
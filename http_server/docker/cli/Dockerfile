FROM elixir:1.6.5

#todo: add rebar
ENV MIX_HOME=/opt/mix \
    HEX_HOME=/opt/hex \
    HOME=/opt/app

RUN mix local.hex --force

RUN mkdir -p /opt/hex/packages/hexpm

RUN chmod -R 777 /opt/mix /opt/hex

#root/.mix/archives/hex-0.17.7

# ENV MIX_HOME=/root/.mix \
#     HEX_HOME=/root/.mix/archives/hex-0.17.7/hex-0.17.7

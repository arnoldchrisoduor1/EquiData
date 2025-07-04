# Using the official Elixir image.
FROM elixir:1.15-alpine

# Installing and building the dependancies.
RUN apk add --no-cache build-base npm git python3 postgresql-client

# setting the working directory.
WORKDIR /app

# Installing the hex and rebar
RUN mix local.hex --force && \
    mix local.rebar --force

# copy mix files.
COPY mix.exs mix.lock ./

# Installing the dependancies.
RUN mix deps.get

# Copy the application code.
COPY . .

# complete the application.
RUN mix compile

# Expose the port.
EXPOSE 4000

# default command.
CMD ["mix", "phx.server"]
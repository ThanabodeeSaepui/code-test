FROM node:20-slim AS base

ENV PNPM_HOME="/pnpm"
ENV PATH="$PNPM_HOME:$PATH"

RUN corepack enable

WORKDIR /app

COPY . /app

RUN pnpm i

RUN pnpm run build

# COPY --from=build /app/dist /app/dist

EXPOSE 8000

CMD [ "pnpm", "run", "preview" ]
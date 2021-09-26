# next-with-preact-auth-db-ts [![styled with prettier](https://img.shields.io/badge/styled_with-prettier-ff69b4.svg)](https://github.com/prettier/prettier) [![MIT License](https://img.shields.io/apm/l/atomic-design-ui.svg?)](LICENSE)

![next-with-preact-auth-db-ts](https://og-image.vercel.app/Next.js%20starter%20with%20**Preact**%2C%20**FaunaDB**%2C%20**MDX**%2C%20**React%20Query**%2C%20**NextAuth**%20and%20more.png?theme=light&md=1&fontSize=75px&images=https%3A%2F%2Fassets.vercel.com%2Fimage%2Fupload%2Ffront%2Fassets%2Fdesign%2Fnextjs-black-logo.svg&images=https%3A%2F%2Fapi.iconify.design%2Flogos%2Fpreact.svg%3Fwidth%3D350&images=https%3A%2F%2Fcdn.jsdelivr.net%2Fgh%2Fremojansen%2Flogo.ts%40master%2Fts.svg&images=https%3A%2F%2Fapi.iconify.design%2Fvscode-icons%2Ffile-type-fauna.svg%3Fwidth%3D350&widths=350&heights=auto&heights=250&heights=200&heights=250)

> Next.js starter kit with Preact + Typescript + Tailwind + React Query + NextAuth.js (GitHub Auth + Passwordless) + FaunaDB

## Getting Started: Local Development

- Clone the project

  ```bash
    git clone https://github.com/pbteja1998/nextjs-starter.git
  ```

- Go to the project directory

  ```bash
    cd nextjs-starter
  ```

- Install dependencies

  ```bash
    yarn
  ```

- Create .env.local and change env variables as per the [instructions](#environment-variables).

  ```bash
    cp .env.example .env.local
  ```

- Setup the database by running the following command and pasting the Fauna Secret key when prompted. More details at [fauna-schema-migrate](https://github.com/fauna-brecht/fauna-schema-migrate).

  ```bash
    yarn setup-db
  ```

- Start the server

  ```bash
    yarn dev
  ```

## Environment Variables

To run this project, you will need to add the following environment variables to your `.env.local` file

- `NEXTAUTH_URL`
  - This is the your application URL. Locally, you can set this to `http://localhost:3000`
- `SECRET`
  - Set this to any randomly generated string
- `EMAIL_SERVER`
  - This is the email server string. It's in the format of `smtp://username:password@smtp.example.com:587`. Replace `username`, `password` and `smtp.example.com` with your own credentials.
- `EMAIL_FROM`
  - Your email address from which you are sending emails.
- `GITHUB_ID`
- `GITHUB_SECRET`
  - You need to create a GitHub OAuth App, and get the GITHUB_ID AND GITHUB_SECRET from that app.
  - You can follow [these instructions](https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/).
  - When creating an oauth app for local development, you can set the `Homepage URL` to `http://localhost:3000` and `Authorization Callback URL` to `http://localhost:3000/api/auth/callback/github`
- `LINKEDIN_ID`
- `LINKEDIN_SECRET`
  - You need to create an oauth app for LINKEDIN. You can set the callback URL to `http://localhost:3000/api/auth/callback/linkedin`
- `FAUNADB_SECRET`
  - Create a new fauna server key and set this variable to that key

## FAQ

### How to run Fauna locally?

**Please note that this is completely optional. You can directly create your database in Fauna cloud and directly use the secret you generate there.**

We are using [Fauna Dev](https://docs.fauna.com/fauna/current/integrations/dev) docker container to run Fauna instance locally.

These are the instructions to setup Fauna container locally.

```bash
# Pull the latest Docker container:
docker pull fauna/faunadb:latest

# Verify that the container executes correctly:
docker run fauna/faunadb --help
```

After you installed this, you can start the container using the following command

```bash
docker run --rm --name faunadb -p 8443:8443 -p 8084:8084 fauna/faunadb
```

Please note that this will create a new instance of Fauna everytime you run it, and all the data will be cleared when you stop this container. For other config options and approaches, go through the [documentation](https://docs.fauna.com/fauna/current/integrations/dev).

**Changes you need to do in the template:**

- You have to set `USE_FAUNA_DOCKER=true` in your `.env.local` file
- Everytime you start the docker container, you need to first apply the migrations. You can do it by running `yarn setup-docker-db`.
- More details at [fauna-schema-migrate](https://github.com/fauna-brecht/fauna-schema-migrate) and [Fauna Dev](https://docs.fauna.com/fauna/current/integrations/dev).

## Feedback & Support

For feedback and support, please [open an issue](https://github.com/nberlette/nextjs-starter/issues/new) in this repo.

## License

[MIT](LICENSE) © 2021+ [Nicholas Berlette](https://github.com/nberlette)

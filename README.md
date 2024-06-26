# T3 on Zerops

This is a template to deploy a T3 stack project with next auth + prisma + postgres on [zerops](https://zerops.io).

### Tech Stack Used

- [Next.js](https://nextjs.org)
- [NextAuth.js](https://next-auth.js.org)
- [Prisma](https://prisma.io)
- [Drizzle](https://orm.drizzle.team)
- [Tailwind CSS](https://tailwindcss.com)
- [tRPC](https://trpc.io)

### Importing this project - Fastest Way

Go to Zerops Dashboard, Import Project using the import yaml mentioned below

```yaml
project:
  name: zerops-t3

services:
  - hostname: t3stack
    type: nodejs@20
    buildFromGit: https://github.com/nermalcat69/t3-zerops
    ports:
      - port: 3000
        httpSupport: true
    enableSubdomainAccess: true
    minContainers: 1
    envSecrets:
      # Automatically connects to the pg with the hostname "db" in the project
      DATABASE_URL: postgresql://${user}:${password}@db:5432
      # Replace with your url later in your nodejs service's
      # environment variables section
      # eg: yourproject.zerops.app, testproject.com, test.example.com
      NEXTAUTH_URL: http://t3.zerops.xyz
      # You can generate your secret using `openssl rand -base64 32` in your terminal
      NEXTAUTH_SECRET: gw7RPnvDKc4lohNT/8LdMe1bKBuURAW4gPme7eOYvYs
      # Grab your client secret and id from https://discord.com/developers/applications
      DISCORD_CLIENT_ID: discord-client-id
      DISCORD_CLIENT_SECRET: discord-client-secret
  - hostname: db
    type: postgresql@16
    mode: NON_HA
    priority: 1
```

## Facing issues while Deploying

Make sure you've added

- [ ] Environment Variables mentioned in [.env.example](https://github.com/Nermalcat69/T3-Zerops/blob/main/.env.example).

For more info you can use [Zerops Docs](https://docs.zerops.io/) or reach out for help at their [Discord Server](https://discord.gg/RzaeZZJVEj).

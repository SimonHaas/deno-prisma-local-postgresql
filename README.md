# deno-prisma-local-postgresql

Attempt to get deno and prisma working with a local postgresql database.

https://github.com/denoland/examples/blob/main/with-prisma/readme.md

```bash
deno run -A npm:prisma@latest init
deno run -A npm:prisma@latest db push # works
deno run -A npm:prisma studio
deno run -A npm:prisma generate
deno run -A prisma/seed.ts # fails
```

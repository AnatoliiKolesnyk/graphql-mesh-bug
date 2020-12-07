Simple repo to reproduce the problem with `explode: true` query parameter.
Run this command to start the GraphQL Mesh server:

`npm run start:mesh`

and this command to start the server documented in OpenApi yaml:

`npm run start:server`

Open playground at `http://localhost:7778/` and run this query:
```
query Test {
  testExplodeParameter(exploded:["abc", "def"])
}
```

Observe the output in the terminal where the server is running (launched with `npm run start:server`).

**Expected result:** This URL is logged: `/test?exploded=abc&exploded=def`

**Actual result:** The log is `/test?exploded=abc%2Cdef`

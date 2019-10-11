# docker-compose-actions-workflow

This is a GitHub Actions workflow example to demonstrate building and testing a multi-container stack using `docker-compose`.

This sample is based on the [Get started with Docker Compose](https://docs.docker.com/compose/gettingstarted/) documentation.

## GitHub Actions Workflow

**push.yml**
```yml
name: Docker Compose Actions Workflow
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: Build the stack
        run: docker-compose up -d
      - name: Test
        run: docker run --network container:webapp-frontend appropriate/curl -s --retry 10 --retry-connrefused http://localhost:5000/
```

You can browse a run for this example [here](https://github.com/peter-evans/docker-compose-actions-workflow/commit/8fb9500661c318028422f3859c2d6e75dee0b9d9/checks).

For more about testing containers before release see [Smoke Testing](https://github.com/peter-evans/smoke-testing).

## License

MIT License - see the [LICENSE](LICENSE) file for details

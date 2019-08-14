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
    - uses: actions/checkout@master
    - name: Build the stack
      run: docker-compose up -d
    - name: Test
      run: docker run --network container:webapp-frontend appropriate/curl -s --retry 10 --retry-connrefused http://localhost:5000/
```

## License

MIT License - see the [LICENSE](LICENSE) file for details

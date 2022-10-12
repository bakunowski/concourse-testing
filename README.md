# concourse-testing

An example repository demonstrating some capabilities of Concourse CI.

## To run

### Get a local instance of Concourse

In order to run and interact with Concourse locally:

If you're on an M1 machine:

`docker compose -f docker-compose-m1.yaml up`

Otherwise simply:

`docker compose up`

### Web UI

To login to the web UI, please go to `127.0.0.1:8080`. You should see a login
button in the upper right corner. Username is `test` and password is `test`.

### Install `fly` CLI

You can download binaries directly from the web UI, by clicking one of the
icons below "welcome to concourse!"

There are also some oneliners
[here](https://concourse-ci.org/quick-start.html#install-fly).

Otherwise, please consult your package manager of choice.

### Commands

Login to Concourse and setup a target.

`fly -t tutorial login -c http://localhost:8080 -u test -p test`

Fetching PRs from GitHub requires authentication. The easiest way is to
generate a temporary GitHub token for your account. Once you have that, you
have to pass it in as a variable.

`fly -t tutorial set-pipeline -p setup -c pipeline.yml -v token=YOUR_GITHUB_TOKEN`

You might get a deprecation warning here, please ignore it for the purposes of
this demo.

`fly -t tutorial unpause-pipeline -p setup`

### Results

If all goes well you should now be able to see the main pipeline run and setup
more pipelines in the process.

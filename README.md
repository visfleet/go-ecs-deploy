# go-ecs-deploy
Deploy a hosted docker container to an existing ecs cluster

Allows deployment of ECS microservices straight from the command line!

## Installation

```
go get github.com/visfleet/go-ecs-deploy
```

## Requirements

You need:

- Valid AWS credentials for the place you're deploying to (in your ENV)
- An existing task definition - this won't create one for you

## Usage

The full list of options is:

```
Usage of ./go-ecs-deploy:
  -C value
        Slack channels to post to (can be specified multiple times)
  -a string
        Application name (can be specified multiple times)
  -c string
        Cluster name to deploy to
  -d    enable Debug output
  -e string
        Application environment, e.g. production
  -i string
        Container repo to pull from e.g. quay.io/username/reponame
  -r string
        AWS region
  -s string
        Tag, usually short git SHA to deploy
  -t string
        Target image (overrides -s and -i)
  -w string
        Webhook (slack) URL to post to
  -m enable multi container deploy
```

### Example

```
AWS_PROFILE=production go-ecs-deploy \
  -c production \
  -a webapp \
  -i quay.io/username/reponame \
  -e production \
  -s 123456ab \
  -r us-west-2
```

## Development

To update dependencies, open `go.mod` and update package versions. Then run `go mod`.

To build `go-ecs-deploy` locally simply run `make build`.


# taurus

Contains examples of how to run taurus test along with Blazemeter and docker/docker-compose.

## Simple Taurus Test without BlazeMeter account:
- Go to SimpleTaurusTest dir
- run ```bzt 1-simpliest.yml```
- to see results in blazeMeter - add following to reporting section in your yml file.

```
- module: blazemeter
  report-name: Taurus test report
  test: Taurus test
  project: Taurus test project
```

## Simple Taurus Test with Blzemeter account:

```
export BLAZEMETERAPIKEYS = id:key
bzt -o settings.env.BLAZEMETERAPIKEYS=$BLAZEMETERAPIKEYS SimpleTaurusTest/test.yml -cloud
```

## Fake api example

```
bzt apiTest/scenario.yml apiTest/execution.yml
```

## Docker-compose

```
docker-compose run fakeApiTest
docker-compose run simpleTest  //runs with -report flag which shows results in blazemeter
```

## Docker run

```
docker run -it --rm -v $(pwd):/bzt-configs blazemeter/taurus -o settings.env.BLAZEMETERAPIKEYS=$BLAZEMETERAPIKEYS /bzt-configs/SimpleTaurusTest/test.yml -cloud

OR use  "-o modules.blazemeter.token=..." option
```

## Custom dockerfile

```
docker build -t test .
docker run --env BLAZEMETERAPIKEYS -it test
```
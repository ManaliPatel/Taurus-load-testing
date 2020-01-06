
## To run Simple Taurus Test without BlazeMeter account:
- Go to SimpleTaurusTest dir
- run ```bzt 1-simpliest.yml```
- to see results in blazeMeter - add following to reporting section in your yml file.

```
- module: blazemeter
  report-name: Taurus test report
  test: Taurus test
  project: Taurus test project
```

## To run Simple Taurus Test with Blzemeter account:

```
export BLAZEMETERAPIKEYS = id:key
bzt -o settings.env.BLAZEMETERAPIKEYS=$BLAZEMETERAPIKEYS SimpleTaurusTest/test.yml -cloud
```

## using fake api

```
bzt apiTest/scenario.yml apiTest/execution.yml
```

## using docker-compose

```
docker-compose run fakeApiTest
docker-compose run simpleTest  //runs with -report flag which shows results in blazemeter
```

## using docker run

```
docker run -it --rm -v $(pwd):/bzt-configs blazemeter/taurus -o settings.env.BLAZEMETERAPIKEYS=$BLAZEMETERAPIKEYS /bzt-configs/SimpleTaurusTest/test.yml -cloud
```
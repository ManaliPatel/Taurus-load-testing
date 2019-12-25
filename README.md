
## To run Simple Taurus Test without BlazeMeter account:
- Go to SimpleTaurusTest dir
- run bzt 1-simpliest.yml
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
bzt -o settings.env.BLAZEMETERAPIKEYS=$BLAZEMETERAPIKEYS 1-simpliest.yml -cloud
```
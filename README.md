# dockstore-workflow-md5sum-072023

This is an extremely simple workflow used to show how to call a workflow via [Dockstore](http://dockstore.org).

It is a forked version of the [original repository](https://github.com/briandoconnor/dockstore-workflow-md5sum) and was used
for the eLwazi GA4GH Conference in July of 2023.

## Validation

This workflow has been validated as WDL v1.0 and launched using Dockstore 1.14.0.

There is a CWL version included here but that wasn't tested.

## WDL Testing

How to execute this workflow using the WDL descriptor via the Dockstore command line (which calls the `cromwell` command behind the scenes).

### Testing Locally with the Dockstore CLI

This workflow can be found at the [Dockstore](https://dockstore.org), login with your GitHub account and follow the
directions to setup the CLI.  It lets you run a Docker container with a WDL descriptor locally, using Docker and the Cromwell utility.  This is great for testing.

#### Make a Parameters JSON

This is the parameterization of the md5sum workflow, a copy is present in this repo called `md5sum.wdl.json`:

```
{
 "ga4ghMd5.inputFile": "md5sum.input"
}
```

You will see the output noted in the stdout from running the Dockstore CLI:

```
  "outputs": {
    "ga4ghMd5.md5.value": "/private/var/folders/2f/fmr4lkw14_jbdq07g6bfdj400000gp/T/1689017681991-0/cromwell-executions/ga4ghMd5/aca2a221-f444-4ce6-a1f6-e20490eec0fe/call-md5/execution/md5sum.txt"
  }
```

This will tell you the location of the output md5sum file.

You might need to use this "output_file" free `test.json` if you are executing a more strict CWL execution engine like Arvados.


#### Run with the Dockstore CLI

Run it using the `dockstore` CLI locally with the WDL file (great for testing if you make changes locally):

```
# run this locally
$> dockstore workflow launch --entry md5sum.wdl --local-entry --json  md5sum.wdl.json
```


## Publishing

At this point you follow the SOP from the [Dockstore.org site](https://dockstore.org/docs).

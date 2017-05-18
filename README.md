Simple shell wrapper around [aws s3 CLI](http://docs.aws.amazon.com/cli/latest/reference/s3/) to expose subcommands as node steps.

The following steps are available:

* cp
* ls
* mb
* mv
* rb
* rm
* sync

To build the plugin:

    zip -r aws-s3-steps.zip aws-s3-steps

To install the plugin:

    cp aws-s3-steps.zip $RDECK_BASE/libext
    
## Example Job

```yaml
- description: 'Copy the contents of /tmp/stuff to an s3 folder'
  executionEnabled: true
  group: aws-s3-example
  loglevel: INFO
  name: cp
  nodeFilterEditable: false
  scheduleEnabled: true
  sequence:
    commands:
    - configuration:
        access_key: XXXXXXXXXXXXXXXXXXX
        delete: 'false'
        destination: s3://rdprotesting/tmp
        dryrun: 'false'
        quiet: 'false'
        recursive: 'true'
        secret_access_key: keys/s3-examples/my.secretkey
        source: /tmp/stuff
      nodeStep: true
      type: aws-cli-s3-cp-step
    keepgoing: false
    pluginConfig:
      WorkflowStrategy:
        node-first: null
    strategy: node-first
```

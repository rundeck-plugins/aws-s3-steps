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
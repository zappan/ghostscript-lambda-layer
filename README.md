# Ghostscript for AWS Lambda

Scripts to compile Ghostscript (gs) for AWS Lambda instances powered by Amazon Linux 2.x,
such as the `nodejs10.x` runtime, and the updated 2018.03 Amazon Linux 1 runtimes.


## Usage

Absolutely the easiest way of using this is to pull it directly from the AWS Serverless
Application repository into a CloudFormation/SAM application, or deploy directly from
the Serverless Application Repository into your account, and then link as a layer. 

For manual deployments and custom builds, read below...


## Prerequisites

  * Docker desktop
  * Unix Make environment
  * AWS command line utilities (just for deployment)


## Compiling the code

  * start Docker services
  * `make all`

There are two `make` scripts in this project.

  * [`Makefile`](Makefile) is intended to run on the build system, and just starts
    a Docker container matching the AWS Linux 2 environment for Lambda runtimes to
    compile Ghostscript using the second script.
  * [`Makefile_gs`](Makefile_gs) is the script that will run inside the container,
    and actually compile binaries. 

The output will be in the `result` dir.

### Configuring the build

By default, this compiles a version expecting to run as a Lambda layer from
`/opt`. You can change the expected location by providing a `TARGET` variable 
when invoking `make`.

The default Docker image used is `lambci/lambda-base-2:build`. To use a different
base, provide a `DOCKER_IMAGE` variable when invoking `make`.

Modify the versions of libraries or Ghostscript directly in [`Makefile_gs`](Makefile_gs).


### Compiled info

```
ghostscript version 9.27
```


## Deploying to AWS as a layer

Run the following command to deploy the compiled result as a layer in your AWS account.

```
make deploy DEPLOYMENT_BUCKET=<YOUR BUCKET NAME> [PROFILE="--profile <YOUR NAMED PROFILE FROM ~/.aws/credentials>"]
```


### Configuring the deployment

By default, this uses `ghostscript-layer` as the stack name. Provide a
`STACK_NAME` variable when calling `make deploy` to use an alternative name.


## Additional Info

For more information, check out:

  * https://www.ghostscript.com/


## Author

Tomislav Capan


## License

  * These scripts: [MIT](https://opensource.org/licenses/MIT)
  * Ghostscript: <https://www.ghostscript.com/license.html>
  * Contained libraries all have separate licenses, check the respective web sites for more information

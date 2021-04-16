# Ghostscript Lambda Layer for Amazon Linux 2 AMIs

Ghostscript AWS Lambda layer adding PDF files conversion support using ImageMagick.
Bundles Ghostscript 9.54.0.

As a prerequisite, add the ImageMagick support by deploying the
[image-magick-lambda-layer](https://serverlessrepo.aws.amazon.com/applications/arn:aws:serverlessrepo:us-east-1:145266761615:applications~image-magick-lambda-layer)
Lambda layer. Check out https://github.com/serverlesspub/imagemagick-aws-lambda-2
for more information.

This application provides a single output, `LayerVersion`, which points to a
Lambda Layer ARN you can use with Lambda runtimes based on Amazon Linux 2 (such
as the `nodejs10.x` runtime).

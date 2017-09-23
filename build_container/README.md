# k8s-builder

This config rebuilds the Docker container used to perform k8s builds and
uploads to GCR.  This build should be run any time the dependencies defined in
the Dockerfile are updated.

To update run:
```
gcloud container builds submit --config cloudbuild.yaml .
```

## Dependencies

Packages installed on the build container are documented here.

This image is extending the official Google Cloud Builder Docker image.

- **curl** - Used for fetching build dependencies as part of the container
  build.
- **wget** - Used for fetching dependencies as part of the Istio build.
- **gnupg2** - Used for adding public keys for apt repositories.

- **git** - Used to fetch source code from Git repositories.
- **openjdk-8-jdk** - Required by Bazel.
- **python** - Required by Istio build and various dependencies.
- **repo** - Used for fetching multiple source repositories into a single
  workspace.

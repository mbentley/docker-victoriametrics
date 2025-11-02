# mbentley/victoria-metrics

docker image for VictoriaMetrics; direct mirror of `victoriametrics/victoria-metrics` images

## Image Tags

For an up to date list of tags, please refer to the [Docker Hub tags list](https://hub.docker.com/r/mbentley/victoria-metrics/tags). I only tag the `amd64` and `arm64` manifests as I have no needs for the others. The script, which runs daily, will always pull from the GitHub tags API. Other older tags may be available but this script only updates the last five. I'm not sure of the support lifecycle for each version of VictoriaMetrics but they don't seem to release patches for older versions for very long.

For example, if the `v1.128` tag is the latest, I will tag it as `latest`, `1`, and `1.128` so you can always refer to a specific version by it's `major.minor` version.

**Note**: The `latest` tag will always be the same as the newest `major.minor` tag as that is handled automatically in the script. This is what I personally typically use unless there is a bug or a reason to pin to a specific version.

## Why

I've found that the VictoriaMetrics images published in the [victoriametrics/victoria-metrics](https://hub.docker.com/r/victoriametrics/victoria-metrics/) repository on Docker Hub only has specific tags (e.g. - there are no `major.minor` tags) which makes it a pain to stay up to date on the latest bugfix versions. [These scripts](https://github.com/mbentley/docker-victoria-metrics) will run daily to just create manifest tags for the `linux/amd64` images by querying for the latest tag from GitHub, parsing it, and writing manifests with the `major.minor` version only.

This allows for using the `major.minor` versions so that you'll always have the latest bugfix versions, such as:

* `mbentley/victoria-metrics:v1.128` is a manifest pointing to `victoriametrics/victoria-metrics:v1.128`

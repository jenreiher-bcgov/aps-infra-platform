# aps-infra-platform

This repository performs two functions:

1. Publishes documentation (inc. press releases) to the API Services Portal

2. Updates the Organization Hierarchy and Namespace assignment (until the UI is complete)

## Publishing

```
docker run -ti --rm -v `pwd`:/work ubuntu:latest

apt-get update
apt-get install -y python3 pip
pip3 install pyyaml requests

export CLIENT_ID=""
export CLIENT_SECRET=""
export TOKEN_URL=""
export PORTAL_URL=""
/work/bin/y2j-put /ds/api/v2/organizations/ca.bc.gov/access /work/organization/access.yaml

/work/bin/y2j-put /ds/api/v2/organizations/ministry-of-citizens-services/databc/namespaces/sp42-test

/work/bin/y2j-put /ds/api/v2/namespaces/platform/contents \
  /work/documentation/owner-journey.yaml \
  /work/documentation/owner-journey.md

/work/bin/y2j-put /ds/api/v2/namespaces/platform/contents /work/press-releases/2021-jun.yaml

```

# mxe-foss 

This repository contains custom built helm charts and images

## Submodule initialisation

After cloning the repo update the submodule

```shell
git submodule update --init --recursive
```

## Rulesets Configuration in ruleset2.0.yaml

### Managing custom made Helm charts in proj-mxe-deps-helm repo

> **_NOTE:_**  Before running the rules for pushing/deleting charts (explained below), API_TOKEN env var has to be set. It is recommended to use the API_TOKEN for mxecifunc as it has access to push/delete charts

- The helm charts that we wish to customise are configured in dependencies.yaml
  Each helm chart has 3 properties
  $chartIdentifier_CHART_NAME
  $chartIdentifier_VERSION
  $chartIdentifier_REPO_URL
  where $chartIdentifier is a unique identifier for the source chart like SELDON_CORE or SERVICE_MESH

- For Downloading configured open source helm charts and saving to $projectRoot/.bob/temp, refer wrapper rule download_all_charts which downloads all configured charts. Alternatively you can also invoke the rules defined in download_all_charts individually

- Once chart is available in temp folder, it can be promoted to helm_charts directory and customisations can be done.
  New additions to helm_charts/ folder are straightforward
  If you have modified version in dependencies.yaml and downloaded a new version, then it is recommended to compare the new Source chart version with the existing Custom chart present in helm_charts dir to selectively promote the necessary updates.
  
- Once customisations are done, the charts can be packaged using the wrapper rule package_all_charts which creates tgz archives in dedicated folders inside $projectRoot/bob

- The customized chart archives can now be pushed to ARM using rules defined in the wrapper rule push_all_charts

- In case fixes have to be applied to already pushed customised chart versions, use the rules defined in wrapper rule delete_all_charts
  to first delete the faulty version from helm repo, and then reupload the fixed chart using steps described above



### Manging custom Images

TODO: Move 3pp-images dir from mxe-core and write convinience rules in ruleset2.0.yaml for their handling


### 3pp OS Patching

TODO: add steps to patch OS versions in 3pp-images custom built by MXE
# kubeflow-test

## How I got this running locally

- Installed `kind` as per https://www.kubeflow.org/docs/components/pipelines/installation/localcluster-deployment/
- `kind create cluster``
- Deployed Kubeflow Pipelines as per https://www.kubeflow.org/docs/components/pipelines/installation/localcluster-deployment/#deploying-kubeflow-pipelines
  - Wait a couple of minutes for step 2 to run successfully. Then the Kubeflow Pipelines UI is accessible on http://localhost:8080/
- Created this folder/repo with `poetry new kubeflow-test``
- Install Kubeflow Pipelines SDK via `poetry add kfp` (installed kfp version 1.8.2 on 31 March 2022)
  - Need to install `ipykernel` to work in a Jupyter Notebook in VSCode: `poetry add ipykernel`
  - Install pandas: `poetry add pandas`
- Follow instructions in https://www.kubeflow.org/docs/components/pipelines/sdk-v2/build-pipeline/ to deploy an example pipeline with SDK v2, in a Jupyter Notebook.
  - In last step https://www.kubeflow.org/docs/components/pipelines/sdk/build-pipeline/#build-your-pipeline, the URL
  for `web_downloader_op` is incorrect. Use: `https://raw.githubusercontent.com/kubeflow/pipelines/master/components/contrib/web/Download/component-sdk-v2.yaml` (a `/contrib` in the URL was missing in the guide.)
  - Compile the pipeline as per instructions.
- In the http://localhost:8080/ Kubeflow Pipelines Web UI, upload and run the compiled `pipeline.yaml`.
  - Or: submit the the pipeline run directly from the notebook, which also works. (Option 2 in the guide.)

  ## TODO

  - I should try to run a more complex pipeline. Maybe something here: https://www.kubeflow.org/docs/started/kubeflow-examples/ (seems to be for SDK v1 though, so might need a bit of adjustments to work).
    - Maybe this is better, since using SDK v2: https://www.kubeflow.org/docs/components/pipelines/sdk-v2/python-function-components/
  - Try running something similar on Vertex AI Pipelines.
    - Can I get a similar workflow with it? I.e. using pyenv + poetry + VSCode to manage venvs and notebooks?
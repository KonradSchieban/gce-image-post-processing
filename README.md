## GCE Image Postprocessing

This repository contains a sample daisy workflow to run a script on an existing compute engine image
and create a new image from the created instance.

Steps that are being executed in this Daisy workflow (see `image-post-processing-wf.yaml`):
 * Create Disk from an existing GCE image
 * Create an instance from the previously created disk and run a startup script
 * Wait for a signal in the startup script to complete
 * Shutdown the instance
 * Create a new image from the instance's disk
 * Remove previously created instance

### How to run the workflow

 * A sample Cloud Build configuration file is provided in the repo.
 * Update the input variables for Cloud Run based on your requirements.
 * Update the script `script.ps1` with the configurations that you want to run on the image.
 * Check the workflow file `image-post-processing-wf.json` for the expected success signal in the script and update it accordingly.
 * Run the Cloud Build workflow using `gcloud builds submit . --worker-pool=projects/<your project>/locations/<region>/workerPools/<pool name> --region <region>`
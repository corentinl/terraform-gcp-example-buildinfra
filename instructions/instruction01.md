Open Google Cloud Shell editor with our blank Terraform project alreday cloned in it thank to the button below:  
[![Open in Cloud Shell](https://gstatic.com/cloudssh/images/open-btn.svg)](https://shell.cloud.google.com/cloudshell/editor?cloudshell_git_repo=https://github.com/corentinl/terraform-gcp-example-blank.git)

# Prerequisites

In `provider.tf`:
- Make sure to replace <REPLACE_ME_WITH_SERVICE_ACCOUNT_KEY_PATH> with the path to the service account key file you downloaded
- Make sure to replace <REPLACE_ME_WITH_GCP_PROJECT_ID>" with your project's ID

# Goals
For this exercise we want to provision 2 resources:
- a service account
- a Google Compute Engine Instance with instance type `f1-micro` and associated with the previously terraformed service account.

The Terraform resources you will need from the Google procider will be the following:
- [google_service_account](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/google_service_account)
- [google_compute_instance](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_instance)


# Write some tf configuration

Open main.tf in your text editor, and write the 2 required resource
```hcl
resource "google_service_account" "WRITE YOUR RESOURCE NAME" {
  // set here the required attribute
}

resource "google_compute_instance" "WRITE YOUR RESOURCE NAME" {
  // instance required attribute like name, machine_type and zone

  boot_disk {
    // required attributes for boot disk here
  }

  network_interface {
    // required attributes for network interface here
  }

  service_account {
    // set the required attribute of the service_account associated to the instance
  }
}

```

Complete this configuration appropriately.

# Execute Terraform

### Initialize Terraform  
(dl required dependicies, init backend conf)
```bash
terraform init
```

### Plan
```bash
terraform plan -out theplan
```
verify that 2 resources will be provisioned only


### Apply  
When satisfy with the plan run the apply command
```bash
terraform apply theplan
```

### Destroy (Optional)   
To get rid of all previously provisioned resources run
```bash
terraform destroy
```
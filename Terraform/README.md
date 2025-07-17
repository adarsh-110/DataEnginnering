

# GCP Software Development Kit: 
  Google Cloud Platform SDK is a collection of tools and libraries that allow you to interact with Google Cloud Platform from Local Machine directly using terminus or scripts. It gives access to web services without using the web console for automation, scripting and IAC tools like terraform.
  Common tools in GCP SDK:
  1. gcloud: Main CLI tool to manage GCP resources
  2. gsutil: To manage google cloud storage
  3. bq: To manage google bigquery dataset

  # Steps to be followed for using GCP:
    1. Install the GCP SDK by running its exe file.
    2. Run "gcloud auth application-default login" to get redentials for authetication of GCP services when accessing from local system. The credentials will be saved locally on a json file and will be used whenever a tool wants to access the GCP services.
    3. Use the following to set the billing project when using GCP resources: "gcloud auth application-default      set-quota-project zoomcamp-465606"
    


# Terraform: Install terraform on the system using the exe file or from CLI command.

# Terraform Repo:

    1. main.tf File:
        1. Data Lake: Data Lake is a kind of folder in the cloud which is used for storing raw, ustructured data which lands into the landing zone from different sources.
        2. Big Query Dataset: It is used for storing structured, tablewise data after applying ETL operations on the raw data using some tool like Apache Spark.
        3. The provider credentials for data lake and big query dataset also needs to be specified which is GCP in our case.

        1. Config of Data Lake Bucket:
            a) Storage: This tells us how data is stored, accessed, managed. Standard acceses are frequent and costly whereas infrequent accesses (nearline, coldline, archive) are cheaper. Uniform Bucket Access makes IAM roles the basis of accesibilty for all objects, instead of defining access contril for individual objects.
            b) Lifecycle Rules: This tells us how the data will be discarded after certain period of time 
            c) force_destroy= True : It tells us to delete the bucket even if its having objects in case a deletion is requested
        2. Config of Big Query Dataset:
            We dont need to define configurations for it since it contains structured data which can be controlled directly. However , IAM based access controls and deletion rules can be still provided.

    2. variable.tf file: The variable.tf file is used for storing the reference names/values of different configuration parameters which will be used in the provider.tf and main.tf. This way, we only need to change the reference of these parameters rather than changing all their values across different files. Various variables in this file are:
        a. credentials: Used for storing the address of GCP login credentials on our local system.
        b. project: project ID to understand where to deploy the resources
        c. region: GCP region where resources will be deployed
        d. location: GCP multi region or region setting used for services like BigQuery and Cloud Storage
        e. bq_dataset_name: name assigned to the bigquery dataset
        f. gcs_bucket_name: global unique name for cloud storage bucket
        g. gcs_storage_class: storage class of bucket, Common Values: "Standard", "Nearline", "CloudLine", "Archive"





# Use AWS Batch


### Why do this
 - Scale your analysis using [`AWS Batch`](https://aws.amazon.com/batch/) to manage compute resources

### What is this
 - USE AWS S3 + AWS Batch + custom code + Athena to create **serverless** end-to-end scalable genomic analysis jobs

   - USE **AWS Batch** to orchestrate scalable genomic analysis running EC2 **without** manually configuring scaling of your compute cluster. The API is designed to be a backend for bioinformatics tools (ex. dsub) or systems (cromwell), by providing job scheduling for Docker-based tasks that perform secondary genomic analysis by running container images on one or more EC2 Virtual Machines. Typical secondary analysis jobs include filtering raw reads, aligning and assembling sequence reads, and QA and variant calling on aligned reads.

   - USE **Athana** to analyze variants using the SQL query language.

### Key considerations
 - This is a serverless solution because you work with services or API endpoints and you do NOT configure or manage clusters of VMs or containers
 - Forecast & verify service costs for your analysis jobs --particularly for BigQuery. This is important so that you can inadvertently avoid overspending, which can hapen based on both the data size and computational complexity of your analysis

### How to do this
 USE the [Quick Start](https://cloud.google.com/genomics/quickstart) to run a pipeline that uses the Pipelines API to create an index file (BAI file) from a large binary file containing DNA sequences (BAM file)

 -----


### How to verify you've done it
 - Run your analysis, monitor for correct results (view files in your output bucket)
 - Monitor for service cost, execution time and adjust to meet your requirements


### Other Things to Know
 - Google AWS Batch is still called Google Pipelines/Genomics API in some of the documentation
 - There are two major versions of the this API - v1 and v2
 - The pipeline can run with unaligned BAM files stored in Cloud Storage
    - If your files are in an aligned BAM or FASTQ format, then you must convert them to BAM
    - You can convert your input files locally, or you can use the AWS Batch to convert them in the cloud
 - There are a number of bioinformatics libraries (cromwell, Nextflow....) that are designed to work WITH AWS Batch

### How to learn more
 - 📘 read AWS Batch reference architecture - [link](https://cloud.google.com/solutions/genomic-data-processing-reference-architecture)
 - 📘 read AWS Batch scenarios - [link](https://cloud.google.com/genomics/docs/tutorials/)
 - :octocat: 4 AWS Batch examples in Jupyter notebooks - [link](https://github.com/googlegenomics/datalab-examples/tree/master/datalab/genomics)
 - 📘 use QwikLabs to try out AWS Batch - [link](https://www.qwiklabs.com/focuses/589?parent=catalog)
 - :octocat: see example AWS Batch usage with genomics tools - [link](https://github.com/googlegenomics/pipelines-api-examples)
 - 📘 read End-to-end pipeline patterns and documentation - see the Google Genomics Cookbook -- http://googlegenomics.readthedocs.io/en/latest/
 - 📘 AWS Batch includes a the ability to manager number of AWS services, the key service being EC2.  
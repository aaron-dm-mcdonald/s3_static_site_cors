# S3 Static Site with a backend S3 hosting images 

## Overview

Two S3 Buckets are provisioned and made public with bucket policies. The bucket named "frontend" is configured as a static website. The bucket named "host" is configured with cross-origin support (CORS). Terraform provisions both buckets, the objects needed in each, and the IAM policies. 

The index.html page in "frontend" is written as a terraform template (.html.tmpl) and is dynamically rendered with the templatefile() function to reference the "host" bucket's images so that CORS support can be demostrated. 

The index.html file is rendered by terraform as an example of the templatefile() features in the project directory. The host object files and frontend website endpoint are outputed. 

## Workflow
1) git clone
2) cd 
3) terraform init
4) terraform validate
5) terraform plan
6) terraform apply -auto-approve



## Project Structure

- ./s3_static_site_cors
    - .gitignore
    - 0-var.tf
    - 1-auth.tf
    - 2a-bucket.tf
    - 2b-bucket.tf
    - output.tf
    - README.md
    - website/
        - frontend/
            - error.html
            - index.html.tmpl
            - styles.css
        - host/
            - images/
                - image-1.jpg
                - image-2.jpg
                - image-3.jpg
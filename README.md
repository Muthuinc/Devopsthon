# Devopsthon

i used git jenkins ansible and terraform also docker, i implemented the git submodule concept. seperation of config files from the application files. so that as a devops person i can maintain a clean copy of the config files in aseperate repo.

in the pipeline we created the image , pushed it to docker repo, instance creation done by terraform, config made by ansible.

This pipeline is created on the assumption of deploying the application for the first time in aws cloud. as you mentioned in the description, the company has struggled because of he manual deployment they had. so assumed they are moving to cloud for the first time, so i created everything from VPC to ec2.

I was trying the create auto scaling and loadbalancer in the terraform itself as a another step, but i created them manually because i ran out of time. almost 80% of work done in automation.

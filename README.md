# ECS Cluster Cloud Formation

A collection of cloud formation templates and user data scripts which enable
the creation of an ECS Cluster backed by AWS Elastic File System (EFS)

## ECSClusterWithEFS.template

Creates an ECS Cluster within specified subnets in a VPC. The cluster is using an
auto scaling group which triggers based on Memory Reservation / Utilization.
This ensures that the cluster size increases/decreases based on overal memory usage/reservation
of the services deployed to the cluster.

This template also creates an ECS Service Role which is exported. This role can be reused by all services
running on the cluster.

The cluster template takes in the name of an EFS stack (`EFSWithMountTarget.template`) to
enable each container instance to mount the EFS volume on boot/init

## EFSWithMountTarget.template

Creates an Elastic File System along with Mount Targets in two subnets (in distinct AZs)

Once you create this stack, you can reference it when creating an ECS cluster to have container instances mount the EFS volume. 
 


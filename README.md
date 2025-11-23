🚀 Terraform Roboshop Component Module

This repository contains a Terraform module used to provision and configure EC2 instances for individual Roboshop application components. Each component (like cart, user, catalogue, payment, etc.) can consume this module to deploy its own infrastructure in a consistent, reusable way.

The module is designed to simplify the creation of EC2 instances along with required networking, security, and configuration steps. It is intended to be used as a remote Terraform module from other Roboshop environment repositories (such as terraform-roboshop-infra or 90-components).

📌 About This Module

The terraform-roboshop-component module provides:

Automated creation of EC2 instances for Roboshop services

Component-specific configuration via user data / provisioning

Consistent naming, tagging, and IAM standards

Easy reusability across multiple Roboshop components

A Git-backed module that can be versioned and reused in multiple environments

This module is consumed remotely using Git and can be referenced directly in any Roboshop component environment without copying code.

🔗 How to Use This Module

In the 90-components repository (or any environment), you can call this module like:

module "component" {
  source = "git::https://github.com/kkumaraix-max/terraform-roboshop-component.git?ref=main"

  component_name = var.component_name
  instance_type  = var.instance_type
  environment    = var.environment
  vpc_id         = var.vpc_id
  subnet_id      = var.subnet_id
  security_group_ids = var.security_group_ids
}


This pulls the module directly from your GitHub repo and deploys a fully configured EC2 instance for that component.
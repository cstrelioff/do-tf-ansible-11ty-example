SHELL=/bin/bash

# get digitalocean token
DO_TOKEN := $(shell secret-tool lookup token digitalocean)

# a default announcement
define ANNOUNCE_BODY
Makefile for terraform and ansible commands.

Terraform

tf-init: terraform init [ this should be run first! ]

tf-plan: terraform plan

tf-apply: terraform apply [ you will have to type 'yes' ]

tf-refresh: terraform refresh

endef

export ANNOUNCE_BODY
all:
	@echo "$$ANNOUNCE_BODY"

tf-init:
	@ terraform init

tf-plan:
	@ terraform plan -var "do_token=$(DO_TOKEN)"

tf-apply:
	@ terraform apply -var "do_token=$(DO_TOKEN)"

tf-refresh:
	@ terraform refresh -var "do_token=$(DO_TOKEN)"

tf-destroy:
	@ terraform plan -destroy -out=terraform.tfplan -var "do_token=$(DO_TOKEN)"

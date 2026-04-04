# Configuration Catalog Guide

## Purpose
This guide explains how to use and maintain the finance-config-catalog repository.

## What Belongs Here
- Mapping definitions (field mappings, debtor mappings, VAT mappings, account mappings)
- Control register (control matrix)
- Journal entry templates
- Fixed asset configuration and rules
- Exception category definitions
- Close checklist registers
- Inventory documentation

## What Does NOT Belong Here
- Executable code (belongs in finance-automation)
- Governance rules (belongs in finance-product)
- Operational runbooks (belongs in finance-runbooks)
- Issue/PR templates (belongs in finance-templates)

## How to Make Changes
1. Create a feature branch
2. Make the configuration change
3. Submit a PR
4. Finance Lead reviews and approves
5. Merge to main

## Naming Conventions
- Use lowercase with hyphens for file names
- Use descriptive names that indicate content
- Keep folder structure flat within each category

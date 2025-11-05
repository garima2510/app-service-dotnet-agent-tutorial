---
mode: agent
description: 'Create Azure DevOps Issue for errors present in the log analytics workspace.'
tools: ['Azure MCP/monitor', 'ado/wit_add_work_item_comment', 'ado/wit_create_work_item', 'ado/wit_update_work_item']
---
# Find the error logs from Log Analytics Workspace and create Azure DevOps Issue

Your goal is to create Azure DevOps Issue for errors present in the log analytics workspace.

## Process

1. Use `Azure MCP/monitor` to find the latest error log from the log analytics workspace {{workspace_name}} present in subcription id {{sub_id}} and resource group {{rg_name}}.
2. Use the subscription ID as the parameter to identify the log analytics workspace
3. Use the table 'AppServiceHTTPLogs' to find error logs.
4. Find at most 3 suggestions for fixing the issue using this error log
5. Create new issue using the `ado/wit_create_work_item` tool in the {{ado_project_name}} project in {{ado_org_name}} organization. 
6. Make sure to add all details and the suggestions in 'System Info' field if this is a bug creation in Azure DevOps. 
7. Return the URL of the created issue.

## Requirements

- Single issue for the complete error detail
- Clear title identifying the error detail

## Issue Content

- Title: Title from the error log
- System Info: Problem statement, proposed solution, and context
- Labels: issue, bug

# Tooling for `test_strictness_level` migration

This directory contains scripts that can help us manage the migration of connectors's `acceptance-test-config.yml` to `high` test strictness level.
Before running these scripts you need to set up a local virtual environment in the **current directory**:
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```
## Requirements
* [GitHub CLI](https://cli.github.com/) (`brew install gh`)

## Create migration issue for GA connectors (`create_issues.py`)
This script will create one issue per GA connectors to migrate to `high` test strictness level.

### What it does:
1. Find all GA connectors in `../../../../../airbyte-config/init/src/main/resources/seed/source_definitions.yaml`
2. Generate an issue content (title, body, labels, project), using `./templates/issue.md.j2`
3. Find an already existing issue with the same title.
4. Create the issue and return its url if it does not exist.

Issues get created with the following labels:
* `area/connectors`
* `team/connectors-python` 
* `type/enhancement` 
* `test-strictness-level`

Issues are added to the following project: `SAT-high-test-strictness-level`

### How to run:
**Dry run**:
`python create_issues.py`

**Real execution**:
`python create_issues.py --dry False`


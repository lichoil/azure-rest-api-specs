# Python HybridCompute

These settings apply only when `--python` is specified on the command line.
Please also specify `--python-sdks-folder=<path to the root directory of your azure-sdk-for-python clone>`.
Use `--python-mode=update` if you already have a setup.py and just want to update the code itself.

``` yaml $(python)
python-mode: create
python:
  azure-arm: true
  license-header: MICROSOFT_MIT_NO_VERSION
  payload-flattening-threshold: 2
  namespace: azure.mgmt.hybridcompute
  package-name: azure-mgmt-hybridcompute
  clear-output-folder: true
```
``` yaml $(python) && $(python-mode) == 'update'
python:
  no-namespace-folders: true
  output-folder: $(python-sdks-folder)/hybridcompute/azure-mgmt-hybridcompute/azure/mgmt/hybridcompute
directive:
  - remove-operation: 
    - Machines_Reconnect
    - Machines_CreateOrUpdate
    - Machines_Update
```
``` yaml $(python) && $(python-mode) == 'create'
python:
  basic-setup-py: true
  output-folder: $(python-sdks-folder)/azure-mgmt-hybridcompute
directive:
  - remove-operation: 
    - Machines_Reconnect
    - Machines_CreateOrUpdate
    - Machines_Update
```

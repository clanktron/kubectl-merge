# Kubectl-Merge

A tiny script for easy merging of kubeconfig files.

## Usage

```bash
# merge file1 with current KUBECONFIG path into a single file at ~/.kube/config
kubectl merge file1
# or
# merge file2 kubeconfig into file1 kubeconfig
kubectl merge file1 file2
```

## General Notes

- the script automatically makes a backup of your target kubeconfig
- make sure you don't have conflicting cluster/user/context names in any of your files as this script does perform any special handling for such

---

## Roadmap

`kubectl config` is missing some crucial pieces that would make kubeconfig management much easier.
This script is kinda a halfway solution for such.
I plan on replacing this project with a go binary that uses the official k8s libraries.
The final plugin should be able to do somemthing like the following:
```
Usage: kubectl trueconfig <command> <arg>
Commands:
  delete-all <name>                   Delete all entries (cluster/user/context) with the given name
  merge <config>                      Merge the specified kubeconfig file into the current config
  rename-all <name> <new-name>        Rename all entries (cluster/user/context) with the given name
  rename-cluster <name> <new-name>    Rename the cluster with the given name
  rename-user <name> <new-name>       Rename the user with the given name
```

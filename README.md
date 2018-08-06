## Kubernetes Demo

MASTER_MEM=1200 NODES=1 NODE_MEM=6800 vagrant up

# Kubernetes
- Add docker hub credentials to Kubernetes Secrets
```
kubectl create secret generic dockerhub-username-secret --from-literal=USERNAME=davidainslie

kubectl create secret generic dockerhub-password-secret --from-literal=PASSWORD=<password>
```

# Artifactory
http:/172.17.8.101:31010

Password - continuousdelivery

# SSH
```
mkdir -p keys && ssh-keygen -t rsa
```
when the message "Enter file in which to save the key (/Users/davidainslie/.ssh/id_rsa)" shows, type:
```
keys/id_rsa
```
and all other fields can be blank.

If you list the "keys" directory, there is the private key "id_rsa" and the public key "id_rsa.pub".

Copy contents of public key:
```
pbcopy < id_rsa.pub
```

- In Github: Settings > SSH and GPG keys > New SSH key
- Fill the title with "jenkins", paste public key
- Add SSH Key

Store the private key "id_rsa" as a Kubernetes secret:
```
kubectl create secret generic github-private-key-secret --from-file=id_rsa
```
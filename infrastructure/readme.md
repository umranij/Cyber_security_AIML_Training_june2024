# step 1 :
  
``` 
Login to killercoda.com and enter CKA lab environment 

```


```
Create file example1.yaml

apiVersion : v1
kind : Pod
metadata : 
  name : tomcat-pod 
  labels :
    app : tomcat 
    tier : dev

spec : 
  containers :
    - name : tomcat-container 
      image : vishymails/tomcatimage:1.0 

```


```

4  kubectl get nodes 
    5  kubectl get pod s
    6  kubectl get pods
    7  cat > example1.yaml    # to create document on killer lab machine 

    8  ls
    9  kubectl create -f example1.yaml
   10  kubectl get po 
   11  kubectl describe pod tomcat-pod 
   12  history 

```

```
Create nec namespace 

 13  kubectl get ns 
   14  kubectl get po -n default 
   15  kubectl get po -n kube-system
   16  kubectl create ns nec 
   17  kubectl get ns 

```


```
Create private key and Certificate Signing Request

 19  openssl genrsa -out nec-adm.key 2048
   20  openssl req -new -key nec-adm.key -out nec-adm.csr
   21  ls

```


```
to create certificate signing request get base64 info from the csr file 

cat nec-adm.csr | base64 | tr -d "\n"

you get 



LS0tLS1CRUdJTiBDRVJUSUZJQ0FURSBSRVFVRVNULS0tLS0KTUlJREFEQ0NBZWdDQVFBd2dZWXhDekFKQmdOVkJBWVRBa2xPTVJJd0VBWURWUVFJREFsTFlYSnVZWFJoYTJFeApFakFRQmdOVkJBY01DVUpoYm1kaGJHOXlaVEVQTUEwR0ExVUVDZ3dHUlVSVExtRnBNUXN3Q1FZRFZRUUxEQUpCClNURU1NQW9HQTFVRUF3d0RRbFpTTVNNd0lRWUpLb1pJaHZjTkFRa0JGaFIyYVhOb2VXMWhhV3h6UUdkdFlXbHMKTG1OdmJUQ0NBU0l3RFFZSktvWklodmNOQVFFQkJRQURnZ0VQQURDQ0FRb0NnZ0VCQU5DVURQdGZzQUJmT2tBZgpzaVNmWWF2WXNXOG1HVmNCQnV5ckF1KzRxWWtiWkVqcWZVRGVWdTI4UVJzUjNrVEFjWjEzVk5qeThRMEIvbU53CjlLNlpWbE1IR0htc1dTelpENDM0Vzh3MzdyUitkSFcwSFI2b0lCcHBsam16enZabmhrSnVrTGtYQ1hhNG9WRk0KWk5Cc251cnlYd01SRlhRU0FNVFpvOEdiRk1FSXUrTXFZVFgwaFFBTG0yQnNKZGVLRW1VZnNZelkzMEg0cmtQSApZY2VJVDZ0d0dKbEthZm1EbG5wV2tUVVJjNm9UcW0yVi94cHA4aVVySVJXY21TL2dtVGJLaDB3anRROWdsVFdzCkhEeHZGWGVjVmJDUHNQWllrZ3RQelpCbUp1Z2kwNk5XZ1F3VlNyN3dpL0Myd2VTVjFCa2FhUS9VRVV3QVg5bTIKZUZWN3d3OENBd0VBQWFBME1CVUdDU3FHU0liM0RRRUpBakVJREFaUGNtRmpiR1V3R3dZSktvWklodmNOQVFrSApNUTRNREhCaGMzTjNiM0prUURFeU16QU5CZ2txaGtpRzl3MEJBUXNGQUFPQ0FRRUFhNmVFeWxrUmpKZDVONm5oClBsVW90Y1lRV3A3Q0pOcDkrQk03ZkRKYTZZMkFQM0tXLzVldlJWU3FaWitpSi8yTldtMGxLZjQrYm8vMFZtbVgKelg2T0J3ZVU2VUZDU1o3cVl2RkpjN25hVjFoRHlteWlrcXFXTDBITkVWcUdadk9YYmZJNjBNRktEeHYyWnV6SgpISEJlT05ZSUJ0bjY4ekFwL1c1amgwSU9pN1RhSkgybWJUVjdBRmxoSkIzZVhxbndZNUhzRWlsNVYyVGJVaU5jCnJpb0EvRnpDT0lDLzk1R3lkT2ttQ3k0TUZhWEFnenN1TDVYSHpYSGRRdGo1SGpqSFNEMkFMMHpBRmFmanE2WmUKbFArUEN4WmxQVGpLdGJGaHN6VExOK2dZT3MwdjFmelpoZHQvYzhLaGs1ZGFjZWtqZjluU2RNV2NPREEwRTd5VworNG9nRUE9PQotLS0tLUVORCBDRVJUSUZJQ0FURSBSRVFVRVNULS0tLS0K
```


```
apiVersion : certificates.k8s.io/v1
kind : CertificateSigningRequest
metadata :
  name : nec-adm
spec :
  request : LS0tLS1CRUdJTiBDRVJUSUZJQ0FURSBSRVFVRVNULS0tLS0KTUlJREFEQ0NBZWdDQVFBd2dZWXhDekFKQmdOVkJBWVRBa2xPTVJJd0VBWURWUVFJREFsTFlYSnVZWFJoYTJFeApFakFRQmdOVkJBY01DVUpoYm1kaGJHOXlaVEVQTUEwR0ExVUVDZ3dHUlVSVExtRnBNUXN3Q1FZRFZRUUxEQUpCClNURU1NQW9HQTFVRUF3d0RRbFpTTVNNd0lRWUpLb1pJaHZjTkFRa0JGaFIyYVhOb2VXMWhhV3h6UUdkdFlXbHMKTG1OdmJUQ0NBU0l3RFFZSktvWklodmNOQVFFQkJRQURnZ0VQQURDQ0FRb0NnZ0VCQU5DVURQdGZzQUJmT2tBZgpzaVNmWWF2WXNXOG1HVmNCQnV5ckF1KzRxWWtiWkVqcWZVRGVWdTI4UVJzUjNrVEFjWjEzVk5qeThRMEIvbU53CjlLNlpWbE1IR0htc1dTelpENDM0Vzh3MzdyUitkSFcwSFI2b0lCcHBsam16enZabmhrSnVrTGtYQ1hhNG9WRk0KWk5Cc251cnlYd01SRlhRU0FNVFpvOEdiRk1FSXUrTXFZVFgwaFFBTG0yQnNKZGVLRW1VZnNZelkzMEg0cmtQSApZY2VJVDZ0d0dKbEthZm1EbG5wV2tUVVJjNm9UcW0yVi94cHA4aVVySVJXY21TL2dtVGJLaDB3anRROWdsVFdzCkhEeHZGWGVjVmJDUHNQWllrZ3RQelpCbUp1Z2kwNk5XZ1F3VlNyN3dpL0Myd2VTVjFCa2FhUS9VRVV3QVg5bTIKZUZWN3d3OENBd0VBQWFBME1CVUdDU3FHU0liM0RRRUpBakVJREFaUGNtRmpiR1V3R3dZSktvWklodmNOQVFrSApNUTRNREhCaGMzTjNiM0prUURFeU16QU5CZ2txaGtpRzl3MEJBUXNGQUFPQ0FRRUFhNmVFeWxrUmpKZDVONm5oClBsVW90Y1lRV3A3Q0pOcDkrQk03ZkRKYTZZMkFQM0tXLzVldlJWU3FaWitpSi8yTldtMGxLZjQrYm8vMFZtbVgKelg2T0J3ZVU2VUZDU1o3cVl2RkpjN25hVjFoRHlteWlrcXFXTDBITkVWcUdadk9YYmZJNjBNRktEeHYyWnV6SgpISEJlT05ZSUJ0bjY4ekFwL1c1amgwSU9pN1RhSkgybWJUVjdBRmxoSkIzZVhxbndZNUhzRWlsNVYyVGJVaU5jCnJpb0EvRnpDT0lDLzk1R3lkT2ttQ3k0TUZhWEFnenN1TDVYSHpYSGRRdGo1SGpqSFNEMkFMMHpBRmFmanE2WmUKbFArUEN4WmxQVGpLdGJGaHN6VExOK2dZT3MwdjFmelpoZHQvYzhLaGs1ZGFjZWtqZjluU2RNV2NPREEwRTd5VworNG9nRUE9PQotLS0tLUVORCBDRVJUSUZJQ0FURSBSRVFVRVNULS0tLS0K
  signerName : kubernetes.io/kube-apiserver-client
  usages :
    - client auth

```

```
 24  cat > certificatesigningrequest.yaml
   25  kubectl create -f certificatesigningrequest.yaml 
   26  kubectl get csr 
   27  kubectl certificate approve nec-adm
   28  kubectl get csr 

```


```
Create role service 

apiVersion : rbac.authorization.k8s.io/v1
kind : Role
metadata :
  namespace : nec 
  name : pod-admin
rules :
  - apiGroups : [""] # core api group
    resources : ["pods"]
    verbs : ["get", "watch", "list", "create", "delete", "update"]

```

```

30  cat > role.yaml
   31  kubectl create -f role.yaml

```

```
Create role binding 






apiVersion : v1
kind : Pod
metadata : 
  name : tomcat-pod 
  namespace : nec 
  labels :
    app : tomcat 
    tier : dev

spec : 
  containers :
    - name : tomcat-container 
      image : vishymails/tomcatimage:1.0 

      




apiVersion : rbac.authorization.k8s.io/v1
kind : RoleBinding 
metadata :
  name : admin-pods 
  namespace : nec 
subjects :
  - kind : User 
    name : nec-adm
    apiGroup : rbac.authorization.k8s.io

roleRef :
  kind : Role 
  name : pod-admin 
  apiGroup : rbac.authorization.k8s.io

  





33  cat > role-binding.yaml
   34  kubectl create -f role-binding.yaml 
   35  kubectl get rolebinding.rbac.authorization.k8s.io
   36  kubectl get rolebinding.rbac.authorization.k8s.io -n nec 
   37  cat > example2.yaml
   38  kubectl create -f example1.yaml
   39  kubectl create -f example2.yaml
   40  kubectl get pods 
   41  kubectl get pods -n nec 
   42  kubectl get pods -n nec --as hacker
   43  kubectl get pods -n nec --as nec-adm
   44  kubectl auth can-i get pods -n nec --as hacker 
   45  kubectl auth can-i get pods -n nec --as nec-adm
   46  kubectl auth can-i list pods -n nec --as nec-adm

```





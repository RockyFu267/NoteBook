# 操作步骤

## 创建sa
kubectl create sa  fuao-test -n fuao-test

## 创建role 仅在指定ns fuao-test下能操作的权限
+ ```
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: fuao-test
  namespace: fuao-test
rules:
- apiGroups:
  - '*'
  resources:
  - '*'
  verbs:
  - '*'
```

## 创建rolebinding
+ ```
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: fuao-test
  namespace: fuao-test
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: Role
  name: fuao-test
subjects:
- kind: ServiceAccount
  name: fuao-test
```

## 获取ca 找到对应的sa的secret 
+ kubectl get secret fuao-test-token-nmtjx -n fuao-test -o jsonpath='{.data.ca\.crt}'

## 获取token
+ kubectl get secret fuao-test-token-nmtjx -n fuao-test -o jsonpath='{.data.token}' | base64 --decode

## 
+ ```
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: <ca>
    server: <k8s-api地址>
  name: fuao.test
contexts:
- context:
    cluster: fuao.test
    user: fuao-test
  name: fuao-test@fuao.test
current-context: fuao-test@fuao.test
kind: Config
preferences: {}
users:
- name: fuao-test
  user:
    token: <token>
```

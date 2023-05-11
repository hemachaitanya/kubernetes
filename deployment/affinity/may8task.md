## config my sql db
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: mysql-cm
data: 
   MYSQL_DATABASE: mysqldb
   MYSQL_ROOT_PASSWORD: rootroot
   MYSQL_USER: nopcommerce
   MYSQL_PASSWORD: rootroot
---
apiVersion: v1
kind: Pod
metadata:
  name: mysql
spec:
  containers:
    - name: mysql
      image: mysql:8
      ports:
        - containerPort: 3306
      envFrom:
        - configMapRef: 
            name: mysql-cm
            optional: false

![images](./Images/33.png)

##Ensure usage of secret in MySQL and configmaps
---
apiVersion: v1
kind: Secret
metadata:
  name: mysql-cms
data: 
  MYSQL_DATABASE: bXlzcWxkYgo=
  MYSQL_ROOT_PASSWORD: cm9vdHJvb3QK
  MYSQL_USER: bm9wY29tbWVyY2UK
  MYSQL_PASSWORD: cm9vdHJvb3QK

---
apiVersion: v1
kind: Pod
metadata:
  name: mysql
spec:
  containers:
    - name: mysql
      image: mysql:8
      ports:
        - containerPort: 3306
      envFrom:
        - configMapRef: 
            name: mysql-cms
            optional: false

![imag](./Images/34.png)

##Create a nop commerce deployment with MySQL statefulset and nop deployment
---
---
apiVersion: apps/v1
kind: Deployment
metadata: 
  name: 'nopcommerce'
  labels:
    name: web
spec:
  minReadySeconds: 3
  progressDeadlineSeconds: 10
  replicas: 1
  selector:
    matchLabels:
      app: web
  template:
    metadata: 
      name: 'noppod'
      labels:
        app: web
    spec:
      containers:
        - name: nopcommerce
          image: hema789/hello:nop-2.0
          ports:
            - containerPort: 5000
              protocol: TCP
          env: 
            - name: MYSQL_SERVER
              value: mysqldb
---
apiVersion: v1
kind: Service
metadata:
  name: sql-nop-svc
  labels:
    app: mysql
spec:
  ports:
    - port: 5000
      name: nopCommerce
      protocol: TCP
    - port: 3306
      name: mysql
      protocol: TCP
  selector: 
    app: mysql
    app: web
  type: LoadBalancer





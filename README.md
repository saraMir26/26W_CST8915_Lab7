# Lab 7 – CST8915 Full-stack Cloud-native Development

## Introduction to Kubernetes Basics

##  Lab Objectives

* Understand the basic structure of Kubernetes YAML files
* Learn how to create Kubernetes resources using kubectl and YAML
* Deploy and manage applications in a Kubernetes cluster

---

##  Demo Video

[YouTube Link](https://youtube.com/shorts/pR5KYraYUJQ)

---

## Multi-Resource Deployment

### Components:

* **RabbitMQ**

  * Message broker
  * Handles communication between services

* **Order Service**

  * Communicates with RabbitMQ

* **Product Service**

  * Provides product-related APIs

* **Store Front**

  * Frontend application exposed to users

---

##  RabbitMQ Configuration Analysis

###  Is RabbitMQ Stateful or Stateless?

RabbitMQ is a stateful application.

It stores:

* Messages (queues)
* Configuration data
* User and connection information

---

### Problem: No Persistent Storage

In this lab, RabbitMQ is deployed without persistent storage.

This means:

* Data is stored inside the container only
* No external storage is attached

---

###  What Happens If the Pod is Deleted or Restarted?

If the RabbitMQ pod:

* Crashes
* Restarts
* Gets rescheduled

Then:

* All messages are lost
* All queues are deleted
* System state is reset

---

### Implications

* Loss of critical data
* Broken communication between microservices
* Unreliable system behavior
* Not suitable for production environments

---

##  Possible Solutions

### 1. Use Persistent Volumes

* Store RabbitMQ data outside the container
* Data survives pod restarts

---

### 2. Use Managed Cloud Services

* Avoid managing infrastructure manually
* Improve reliability and scalability

---

##  Azure Service Bus Evaluation

Using Azure Service Bus can solve the issues identified in this lab.

### Benefits:

* Fully managed messaging service
* Built-in persistence
* High availability
* No data loss on restart
* Automatic scaling

### Conclusion:

Yes, Azure Service Bus effectively resolves the limitations of running RabbitMQ without persistent storage.

---

##  Lessons Learned

* YAML provides better control and reproducibility than kubectl commands
* Stateless vs stateful design is critical in cloud-native systems
* Persistent storage is essential for stateful applications
* Managed cloud services simplify operations and improve reliability



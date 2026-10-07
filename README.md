# CST8915 Lab 3 - Deploying the Algonquin Pet Store on Azure

## Demo Video

YouTube Demo Video: [https://youtu.be/QYkQl3Wuv5c]

## Project Overview

In this lab, I deployed the Algonquin Pet Store using different Azure services.

- The Product Service is deployed on Azure Web App Service.
- The Order Service is deployed on Azure Web App Service.
- RabbitMQ is running on an Azure Virtual Machine.
- The Store Front is running on an Azure Virtual Machine.

Azure Static Web Apps could not be created because of a policy restriction on the student Azure subscription. Our professor allowed us to use a virtual machine for the Store Front as an alternative.

The Store Front communicates with the Product Service to load the products and with the Order Service to place orders. The Order Service then sends the order messages to RabbitMQ.

## Reflection Questions

### 1. What challenges did you encounter when configuring environment variables in the GitHub Actions workflow?

I was not able to use Azure Static Web Apps because of a policy restriction on my student Azure subscription. Because of this, I could not use the GitHub Actions workflow for the Store Front as originally required in the lab. Instead, I deployed the Store Front on an Azure Virtual Machine, as allowed by the professor. I configured the Product Service and Order Service URLs using environment variables in a `.env` file on the VM. One challenge I encountered was making sure the URLs were written correctly. For example, a missing `https://` prevented the Store Front from connecting to the Product Service.

### 2. How does deploying microservices on Azure Web App Service differ from running them locally?

When I run a service locally, it depends on my computer and I have to start and manage it myself. With Azure Web App Service, the application runs in Azure and can be accessed through a public URL. Azure also manages much of the infrastructure for the application. In this lab, the Product Service and Order Service could communicate with the other components without running on my local computer.

### 3. Why is it important to use environment variables for configurations in a cloud environment?

Environment variables allow configuration values to be separated from the application code. This makes it easier to change URLs, ports, and connection information without changing the source code. They are also useful when the same application runs in different environments. Sensitive configuration should not be hard-coded directly into the application.

## Service Repositories

- Order Service: https://github.com/Justin-algonquin/order-service
- Product Service: https://github.com/Justin-algonquin/product-service
- Store Front: https://github.com/Justin-algonquin/store-front

## Deployment

- Product Service: Azure Web App Service
- Order Service: Azure Web App Service
- RabbitMQ: Azure Virtual Machine
- Store Front: Azure Virtual Machine

## Notes

The complete application was tested successfully. The Store Front loaded the products from the Product Service, an order was placed through the Order Service, and the new order message appeared in the RabbitMQ `order_queue`.

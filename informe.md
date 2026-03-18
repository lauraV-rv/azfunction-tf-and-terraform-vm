## Laboratory Report

Initially, the Microsoft Azure account was accessed using the az login command, which allowed the session to be authenticated and enabled access to the subscription that would be used to deploy the infrastructure.
Then, work was carried out on the repository provided for the lab, which contained the infrastructure definition through Terraform files. These files included the necessary configuration to deploy an Azure Function along with its associated resources.

Once inside the project folder, the terraform init command was executed. This command initialized the Terraform project, downloaded the Azure provider, and prepared the environment to correctly interpret the .tf files. After that, terraform validate was executed in order to verify that the syntax and structure of the configuration were correct before proceeding with the deployment.

Next, terraform plan was executed. This command shows a preview of the resources that Terraform intends to create in Azure based on the defined configuration. Then, terraform apply was executed, which is the command responsible for applying the changes and effectively deploying the infrastructure in the cloud.
<img width="1919" height="1079" alt="image (2)" src="https://github.com/user-attachments/assets/8a74cc29-f0ff-453c-acfd-372cd6320148" />

During this process, an issue arose related to the region configured for the deployment. Initially, the infrastructure could not be created because the region defined in the variables.tf file was not allowed by the policies of the Azure subscription used in the lab. To solve this problem, the location variable was changed to a valid region. In this case, eastus2 was used, which allowed the deployment of the resources to continue.

In addition, it was necessary to change the function name to avoid conflicts with a name that was already in use. For this reason, a new function name was defined: azfunclau2. With these two adjustments, the deployment was completed successfully.

Once the execution of terraform apply was finished, Terraform displayed the output corresponding to the function invocation URL. This URL is generated from the configuration defined in the outputs.tf file and allows direct access to the HTTP endpoint of the deployed Azure Function.
<img width="1919" height="1079" alt="image (4)" src="https://github.com/user-attachments/assets/40e7d10f-88bf-4e94-adc6-526040a48f22" />

Later, the function was tested by accessing the generated URL and verifying that it responded correctly. This confirmed that the Function App had been created successfully and that the infrastructure configured through Terraform was working properly.
<img width="1919" height="1020" alt="image (6)" src="https://github.com/user-attachments/assets/154f5df8-6d6d-4086-a524-bc9aea928fb5" />

Finally, the Azure portal was also checked to verify that the resources had been created correctly. There, it was possible to confirm the existence of the resource group, the storage account, the service plan, and the Function App, visually confirming that the deployment was successful.
<img width="1919" height="1022" alt="image (5)" src="https://github.com/user-attachments/assets/b0e8a09f-7a8f-4d21-b81e-ff8bd5c382dc" />
<img width="1919" height="1023" alt="image (7)" src="https://github.com/user-attachments/assets/02779cbe-bb9e-4b3c-92dd-4efdc3e38506" />

In conclusion, the lab made it possible to understand the process of deploying an Azure Function in Microsoft Azure using Terraform. It also highlighted the importance of carefully reviewing parameters such as the region and resource names, since these can cause errors during infrastructure creation. Once these aspects were corrected, the function was successfully deployed and its operation was verified both from the console and from the Azure portal.

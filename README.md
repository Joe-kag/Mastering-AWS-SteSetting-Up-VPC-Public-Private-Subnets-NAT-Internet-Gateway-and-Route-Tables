# Mastering-AWS-SteSetting-Up-VPC-Public-Private-Subnets-NAT-Internet-Gateway-and-Route-Tables
Mastering AWS: Step-by-Step Guide to Setting Up VPC, Public &amp; Private Subnets, NAT, Internet Gateway, and Route Tables


1\. A Virtual Private Cloud (VPC) is a secure, isolated network within the public cloud where you control your own private space—like having your own locked apartment in a shared building.

When using Amazon VPC, it's best to place your app and database in a private subnet, and connect the app through a load balancer for security and control.

The screenshot below shows the key resources we're setting up: VPC, Internet Gateway, Subnets, and Route Table—all essential parts of the network architecture.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/9060abe2-156b-43a5-8c8a-12b6df312b86/screenshot.webp?tl_px=0,0&br_px=787,513&force_format=jpeg&q=100&width=919)


2\. First, go to the AWS Console. If you don’t have an account yet, start by creating one.

![1a](https://github.com/user-attachments/assets/39245821-c521-4d6d-8473-c060654c19ea)




3\. On the AWS Console: IN the **search bar at the top**, type **"VPC"** and select **"VPC"** from the filtered results. This will take you to the **VPC Dashboard**. Click on the **“Create VPC”** button to begin creating your virtual network.



4\. - Name your VPC and set the IPv4 CIDR block to “12.0.0.0/16” to define the private IP . You can choose your IP range

- Optionally, you can specify an IPv6 CIDR block if needed.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/85e07909-f9ff-4760-bdf1-4769947edac3/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


5\. - Choose the Tenancy:

  - **Dedicated**: Instances run on dedicated physical servers.

  - **Default**: Instances run on shared physical servers.

- Select **Default** for Tenancy.

- Click **Create** to create the VPC

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/89acd6b7-b540-4b74-b253-c42095bce3a5/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


6\. Great! Now, we have successfully created our VPC named "test-vpc."

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/4ba40e3f-1a2b-49d6-b36f-c144fe0a3811/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


7\. Perfect! Your "test-vpc" is now listed in the VPC dashboard, and its state is **available**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/075a8a20-7dc7-413f-9003-d14ddca3a1b8/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


8\. Next we create **Internet Gateways**.

In the VPC Dashboard, select **Internet Gateways**.

Click on the **Create internet gateway** button.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/b9c995c8-6249-4343-bfc5-8c103734476b/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0) 


9\. Name the Internet Gateway **"IGW-test"**.

Click **Create** to create the Internet Gateway.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/cf53c101-ab81-46e9-9fa0-975e045731ff/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)



10\. Awesome! The Internet Gateway "IGW-test" has been successfully created.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/0a11db6b-5dec-431b-ba2d-6e233ae2d93e/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


11\. Next, attach the **"IGW-text"** Internet Gateway to your VPC:

In the **Internet Gateways** section, select **"IGW-text"**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/dcb2e2de-2cce-4608-b0de-9ad1ca73d34f/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


12\. Click on the **Actions** button and select **Attach to VPC**.

Choose your **"test-vpc"** from the list.

Click **Attach** to complete the process.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/5bb37340-fb88-4cdb-afa5-0182fdf5e5c3/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


13\. Great! Your **"IGW-text"** is successfully attached to the **"test-vpc"**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/73aaa7cc-bf51-4933-9779-7fc38e1ed5b6/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


14\. Next step is creating Subnets -Subnets in a VPC are divided into multiple logical networks. To ensure high availability and resilience, create a subnet in each Availability Zone. Deploying resources across different zones helps protect your applications from potential failures in a single zone.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/a0988529-2299-4a69-92af-db7a3c560cbe/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


15\. In the **VPC Dashboard**, select **Subnets** from the left navigation pane.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/82af6552-dfd3-4905-b995-160f60101b54/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


16\. Click on the **Create subnet** button. To have this dashboard as shown below.

Choose the **"test-vpc"** VPC from the dropdown.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/3979496e-2460-4bc9-ac00-726426792ba4/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


17\. Creating public 

Enter a unique name, e.g., **"test-public-subnet-2a"**.

- Select an **Availability Zone** (choose one for each subnet).
- Set the **CIDR block** to **“12.0.1.0/20”** (within the VPC range)

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/0c7601a5-73c6-41c7-89b5-9b589b345e8f/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


18\. Creating Private

Enter a unique name, e.g., **"test-private-subnet-2a"**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/f4cb8491-ef57-46ad-b9f0-296c33f74d77/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


19\. - Select an **Availability Zone** (choose one for each subnet).
- Set the **CIDR block** to **“12.0.6.0/24”** (within the VPC range)
- Verify your details then click create  subnet.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/8f26f3ee-f084-4705-afc9-73ae535aca6f/user_cropped_screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


20\. Great! We've successfully created our subnets **test-public-subnet-2a** and **test-private-subnet-2a**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/1871161e-13ad-4e8a-8711-afdc9d7f95fd/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


21\. Create a **Route Table**\
A route table contains a set of rules, called routes, that determine where network traffic from your subnet or gateway is directed.

- In the **VPC Dashboard**, select **Route Tables**.
- Click on **Create route table**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/8fdfd0bf-8ec1-49c7-b071-3438f9f30e49/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


22\. - I Named mine  **"RT-test-public"**.
- Then Choose your vpc  **"test-vpc"**.
- Click **Create** to create the route table.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/3bf98ed2-9019-4e1a-ad73-9a45e6864912/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


23\. Good news! We've successfully created our public route table **"RT-test-public"**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/bde50063-08f4-4a73-a5fd-5887e64c5b72/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


24\. Next step is to connect out public route table with internet . We will connect it to the internet Gateway that we created .The destination select "0.0.0.0/0 since is public to connect from anywhere. Then click save changes.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/8fa0cddf-641e-451a-b91c-cd8799954ec9/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


25\. And now we can see that our route table **"RT-test-public"** is active and has internet access.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/a5d67f40-d07a-4643-9a52-f812a3b37480/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


26\. Go to **Route Tables** and select **"RT-test-public"**.

Click on the **Subnet associations** tab

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/00c55878-6920-4ee8-8a63-a978c719590f/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


27\. Next, we connect our route table to the **"test-vpc"**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/8aaf2d70-06b9-4483-891d-4d01fe2b4b20/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


28\. Choose the subnet(s) you want to associate — **"test-public-subnet-2a"**.

Click **Save associations**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/f4d22ccf-77c4-402a-b800-044c09961388/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


29\. This shows our flow from **VPC** to **EC2**, step by step — from creating the VPC, subnets, and Internet Gateway, to configuring the route table and associating it with the subnet — setting the stage to launch an EC2 instance in a fully functional network setup.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/ae79b806-d786-4c8d-9817-93703e7ea209/screenshot.webp?tl_px=0,0&br_px=1063,601&force_format=jpeg&q=100&width=1077)


30\. Now, let's demonstrate how to create a **public EC2 instance**:

Navigate to the **AWS Console**.

Click on **EC2** from the Services menu.

Then click on **Instances** in the left-hand panel.

We’ll go through the setup for the public instance first — then you can try creating the private one on your own to test your understanding!

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/4e1c34b5-90b4-4616-84dd-4406fb2aadde/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


31\. After clicking **Launch Instance**, you'll see the instance configuration dashboard.

Here, I created my public instance named **"test-ec2-public-instance"**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/fa136ec2-e2a9-4190-9e3c-1c9d7c391757/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


32\. In the **network settings** section, be sure to select the correct configurations. I chose my custom VPC **"test-vpc"** and selected the public subnet **"test-public-subnet-2a"** to ensure the instance is launched in the right network segment. To enable internet access, I made sure to set the **Auto-assign Public IP** option to **Enable**. Lastly, I created a new security group named **"test-ec2-SG"** to manage the inbound and outbound traffic rules for this instance.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/dced987b-f1e1-4920-bac1-2dda86b18b61/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


33\. In the **Inbound security group rules**, make sure to select **SSH** to allow remote access to the EC2 instance. For the **Source type**, choose **Anywhere** (0.0.0.0/0) to allow SSH access from any IP address, since this is a public EC2 instance. This will enable you to connect to the instance via SSH from anywhere.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/c4697911-a640-44a8-900f-b79a6a820fe0/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


34\. This demonstrates how to configure the storage.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/e5dd1fb3-8582-48ac-b7c0-2c24e5a600f4/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


35\. After verifying everything, click **Launch Instance**. You can then monitor the progress below as the instance is being created.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/2a2591fa-7a72-4b4f-ba19-95584d4dc6ea/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


36\. And we have successfully launched our instance **"test-ec2-public-instance"**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/bcaad041-175f-4b16-a7ea-f434e09aaf77/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


37\. This shows the summary information of our new EC2 instance, **"test-ec2-public-instance"**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/e8a12b2e-8fff-4ffb-8034-4ad75de81674/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


38\. Click **Connect**, then select **SSH Client** to view the steps on how to access your EC2 instance. If you already have a key, you can skip the key creation step, but if not, you'll need to create one. Just refer to my previous demo for that. Remember, you need to follow the steps below to convert your public key to a private key to establish a secure SSH connection.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/7f5d8587-df2e-4c7c-8bd4-dddcf104b9c9/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


39\. Open your terminal and locate the location of your private key file (typically with a `.pem` extension). Once you’ve found it, follow the steps below to connect to your EC2 instance:

**Navigate to the directory** where your private key file is located

**Change permissions** of the key file to make sure it's secure:  chmod 400 your-key.pem

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/9b7ef809-2c6f-4f5f-9f71-448567438ced/screenshot.webp?tl_px=0,0&br_px=1918,882&force_format=jpeg&q=100&width=1120.0)


40\. **Connect to your EC2 instance** using SSH:

ssh -i "your-key.pem" ec2-user@your-ec2-public-ip

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/88327769-f519-4cdd-94bf-6a358202b948/screenshot.webp?tl_px=0,0&br_px=1918,882&force_format=jpeg&q=100&width=1120.0)


41\. After finishing using your EC2, type **exit** to disconnect from the instance. Then, navigate back to the **AWS Console**. This helps reduce the attack surface area by ensuring no unused resources are running.

The following steps will guide you on how to delete all the resources we’ve created, as it was just for learning purposes and sharing your skills.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/96f4223e-0a4c-45c6-a805-e76b2e634bdb/screenshot.webp?tl_px=0,0&br_px=1918,882&force_format=jpeg&q=100&width=1120.0)


42\. On your EC2 instance, click **Actions**, then select **Manage Instance State**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/b20349d1-866f-4a89-9a59-0783dd840047/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


43\. Next, select **Terminate** and then click **Change Status** to terminate your EC2 instance.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/33f4e91f-616d-4288-8d2c-3713d155a2f9/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


44\. We have successfully terminated our EC2 instance.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/1c1b86d6-4f40-4a93-8ae6-4c03c979bfad/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


45\. Next, we are going to delete the **Route Tables**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/6d35bece-3cec-4d90-ad1f-ee953bbe9e64/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


46\. However, after clicking **Delete route table**, you'll encounter an error because the route table is still associated with a subnet.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/fef1f621-f449-4d1e-b68c-14039402c7c1/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


47\. Disassociate both route tables from their associated subnets, one at a time. This must be done before you can delete the route tables.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/56621f33-9305-4dbe-8331-00a2af771393/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


48\. Now that it’s disassociated, go ahead and delete the **public route table**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/13cc65a2-5bf0-4bce-9395-34ef0c3d6b67/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


49\. We can confirm that we have successfully deleted both of our route tables.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/741b70af-6bdc-4e09-bd97-6edf7b3afc63/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


50\. Next, we proceed to delete our **subnets**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/607f62da-8fc6-4b05-82bb-f9e53fda455a/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


51\. Select the **private subnet**, click **Actions**, then choose **Delete**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/1cdbd790-5133-4f25-987a-fa3eda3af358/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


52\. Type **delete** to confirm, then click **Delete** to remove the subnet.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/d88901f3-6cde-4e70-ac62-1f3db3e6e2aa/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


53\. Select the **public subnet**, click **Actions**, then choose **Delete**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/ad80f7a7-edb5-496b-9f06-30fecd9e730d/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


54\. Type **delete** to confirm, then click **Delete** to remove the subnet.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/80ba4031-3d54-4bde-a543-a17f77c173dd/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


55\. Super! We have successfully deleted our subnets.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/fbadbab3-9bb2-421e-9b4a-5687751af487/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


56\. Next, we proceed to delete the **Internet Gateway** by detaching it from the VPC and then clicking **Delete**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/ea31aaa3-4b85-4c4d-bf29-458f0f9978d4/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


57\. Type **delete** to confirm, then click **Delete** to remove the internet gateway.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/e47822d6-70bc-4bad-8860-6d514d93c97c/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


58\. Next, we proceed to delete the **vpc**.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/a587c81e-41c6-4f91-a833-7b3c25134186/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


59\. Type **delete** to confirm, then click **Delete** to remove the VPC.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2025-04-14/3741d106-fc15-4e6c-a078-b48833e6ef2a/screenshot.webp?tl_px=0,0&br_px=1920,1080&force_format=jpeg&q=100&width=1120.0)


60\. **In conclusion**, this project guided us through the process of creating and configuring a VPC, subnets, Internet Gateway, route tables, security groups, and an EC2 instance, allowing us to set up a secure and functional network environment in AWS. We successfully demonstrated the steps of resource creation, configuration, and cleanup, emphasizing best practices for managing cloud infrastructure. This project has enhanced our skills in AWS networking and EC2 management, providing a strong foundation for future cloud-based endeavors.

# html-ec2-deploy
Deployment on EC2 using GitHub Actions

Deploying a simple static HTML application to an AWS EC2 Ubuntu instance with Nginx as the web server using github actions.

Project Solution:
Launch an EC2 Instance
Name : ubuntuInstance
Ami  :  ubuntu24.0 LTS
Type: t2 micro
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/011feb15-d12d-4fb6-8c2f-9652dc28b0c6" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/79a2fbbf-fb81-47a6-a0ce-cfe616c8f7ac" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/49dba523-4e01-4b53-96f1-c550cab6b923" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/666ddf34-df3a-4655-8b59-4f806cc46b1f" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/68d44429-a5fb-4fbe-95e5-fe78ed04d765" />

Login into ec2 instance:
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/723f985d-ed26-42f7-b0d4-d9358e55fcaa" />

Creating a devops user
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/4ddfa976-95fe-4bb4-8824-e0537a322e58" />

# Switch to the new user
sudo su - devopsuser
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/5ff0741d-e546-4be7-a012-59e4c0ee2263" />

Generate a new SSH key pair in local computer
ssh-keygen -t rsa -b 4096 -C "devopsuser"
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/fbef34a8-ea29-4af1-bd31-2fb58bb75a8b" />

<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/a448b67e-c134-401f-88f9-e5f059b41a24" />

# Copy the public key to EC2
Open  ~/devopsuser.pub  in notepad copy and than paste in ec2Instance at location 
~/home/devopsuser/.ssh/authorized_keys
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/a8ab4078-84ee-4b90-bfb2-bfcb9ba22396" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/b7162158-9876-4d26-861f-c0060b9f3ce1" />

# Login as DevOps user
ssh -i ~/.ssh/devopsuser devopsuser@13.221.20.109
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/baacdead-7af3-4c89-a72f-6048f76cecd4" />

<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/9f5dbca4-bf94-4d08-8b5e-713b472a84c3" />

Create a GitHub Repository
Name : html-ec2-deploy

<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/a7cc088e-532a-4e0a-96e5-7964849c6bc7" />

<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/98dc8fc7-14cc-4432-abdf-498bb07f6c6c" />

Set git repo locally:
echo "# html-ec2-deploy" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/saiyedin786/html-ec2-deploy.git
git push -u origin main

<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/b8f61114-a83c-4ad5-ab72-468015fbab5e" />
Make an index.html file locally:
<!DOCTYPE html>
<html>
<head>
    <title>DevOps Demo</title>
</head>
<body>
    <h1>Hello from GitHub Actions & EC2!</h1>
</body>
</html>

<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/8df4e424-81f2-4e0a-89fc-5901bfc28001" />

Push the code to github repo
Git add .
Git commit – ‘added index.html’
Git push
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/402f1e71-533c-4e6d-8697-4fb1b4ac2c4e" />

Store SSH Key in GitHub Secrets
Navigate to your GitHub repository.
Click on 'Settings' in the repository menu.
Select 'Secrets and variables' > 'Actions'.
Click on 'New repository secret'.
Add the following secrets:
EC2_HOST → 13.221.20.109
EC2_USER → devopsuser
EC2_SSH_KEY → contents of your private key ~/.ssh/devopsuser.pub
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/3522b3ab-7641-46e7-8b5c-f091ecd7fe47" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/cef5a477-28ab-4971-9b16-ac31cc956515" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/63009048-2a38-4705-874e-8eab8411e69a" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/52bab083-60dd-4825-ab53-25e5acfec6af" />
Create GitHub Actions Workflow
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/2414abaa-7e79-4565-a0ef-2ae1678ba5f0" />

Testing :
Make some changes in index.html
Git add .
Git commit –m ‘updated index.html’
Git push

This will trigger github action workflow named deploy.yms
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/607ab7dd-0275-45cf-b93a-521db8411a0d" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/5fb7117c-b5ed-48ee-ae58-3d8a31c218e7" />
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/aef40f80-acbd-491f-a20c-c8d425b071f4" />

After successful completion of all workflow steps open browser  and then check
http://13.221.20.109/
<img width="979" height="552" alt="image" src="https://github.com/user-attachments/assets/ecf7c76f-0e93-455b-96dc-461cf564e661" />




























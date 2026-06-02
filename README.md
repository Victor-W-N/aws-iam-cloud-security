# aws-iam-cloud-security
Hands-on AWS IAM project covering EC2 environment separation, JSON policies, user groups, account aliases, and policy simulation.
<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Victor Njogu  
**Email:** victornjogu24@gmail.com

---

![Image](http://learn.nextwork.org/sincere_maroon_witty_monstera_deliciosa/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate cloud security using AWS Identity and Access Management (IAM). I'm doing this project to learn: 1. Creating EC2 instances 2. IAM policies 3. IAM users and user groups 4. AWS account aliases.

### Tools and concepts

Amazon EC2: launched two virtual servers (production & development), tagged with Env for environment separation. AWS IAM: created a policy, user, group, and account alias to control and test access to those instances. Key concepts I learnt include: Tags: labels used to apply policies to specific resources. IAM policies: JSON rules with Allow/Deny, Actions, and Condition blocks. Users & groups: users = people, groups = permission bundles. Dev vs prod: separate environments to protect live resources. Policy Simulator: test permissions without affecting real resources.

### Project reflection

This project took me approximately two hours. The most challenging part was understanding how to use the IAM Policy Simulator. It was most rewarding to see that I was able to set up two EC2 instances and grant different levels of access.

---

## Tags

### What I did in this step

In this step, I will two amazon EC2 instances because I want to increase an orgarnizations computing power.

### Understanding tags

Tags are labels you can attach to AWS resources to use as descriptors.

### My tag configuration

The tag I’ve used on my EC2 instances is called 1. .env The value I’ve assigned for my instances are 1.Production 2.Development

![Image](http://learn.nextwork.org/sincere_maroon_witty_monstera_deliciosa/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

What I did in this step
In this step, I granted an intern access to the development instance but not the production instance, because we do not want the intern to accidentally shut down the platform or push changes while they are just testing things.

### Understanding IAM policies

IAM policies are rules for who can do what with your AWS resources. They give users, groups, and roles defined permissions specifying what they can and cannot do on certain resources.

### The policy I set up

For this project, I’ve set up a policy using the JSON.

### Policy effect

I created a policy that restricts the intern from accessing the production environment, allowing them to only access the development environment.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy mean: Effect: has two values, Allow and Deny, and indicates whether a policy allows or denies a certain action. Action: a list of actions that the policy allows or denies. Resource: specifies which resources the policy applies to.

---

## My JSON Policy

![Image](http://learn.nextwork.org/sincere_maroon_witty_monstera_deliciosa/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I created an AWS account alias to give the intern an easy way to log in to the AWS Management Console.

### Understanding account aliases

An account alias is a friendly name for your AWS account that you can use instead of the account ID to log in

### Setting up my account alias

Creating an account alias took me about two minutes. My new AWS console sign-in URL is https://my-company-intern.signin.aws.amazon.com/console.

![Image](http://learn.nextwork.org/sincere_maroon_witty_monstera_deliciosa/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I created a dedicated IAM group for all interns and set up a dedicated IAM user for the new intern, so I can manage all permissions from one place and give the intern a way to sign in.

### Understanding user groups

IAM user groups are collections of IAM users. They allow me to control the permissions of multiple users from one place.

### Attaching policies to user groups

I attached the policy I created to this user group, which means all members of this group can access the development EC2 instance but cannot access the production one.

### Understanding IAM users

IAM users are individual people who have access to AWS resources.

---

## Logging in as an IAM User

### Sharing sign-in details

There are two ways to share sign-in details: sending email sign-in instructions, or downloading the .csv file and sending it to them.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed the following error: "Access denied to servicecatalog:ListApplications." This was because of the permissions set earlier, restricting the intern from accessing the production EC2 instance.

![Image](http://learn.nextwork.org/sincere_maroon_witty_monstera_deliciosa/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I will log in using the interns new credentials because I want to test the interns access to the production and development instance.

### Testing policy actions

I tested my JSON IAM policy by attempting to stop both the development and production instances.

### Stopping the production instance

When I tried to stop the production instance, I received a red warning banner stating that I was not authorized to complete the action. This was because the IAM policy restricts the intern from accessing the production environment.

![Image](http://learn.nextwork.org/sincere_maroon_witty_monstera_deliciosa/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

When I tried to stop the development instance, it was successfully stopped. This is because the IAM policy we set up allows the intern access to the development instance.

![Image](http://learn.nextwork.org/sincere_maroon_witty_monstera_deliciosa/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

The IAM Policy Simulator is a tool used to validate and test user permissions without affecting real AWS resources. It is useful for testing permissions in a faster, more efficient way.

### Understanding the IAM Policy Simulator



### How I used the simulator

I set up a simulation for the DeleteTags and StopInstances actions. Both were initially denied. Once I specified the development instance as the resource, the StopInstances action was allowed — confirming that the policy is working as intended.

![Image](http://learn.nextwork.org/sincere_maroon_witty_monstera_deliciosa/uploads/aws-security-iam_069d8a621)

---

---


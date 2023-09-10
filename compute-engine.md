# Compute Engine
Provision and manage virtual machines on Google Cloud.

Create a virtual machine using the Google Cloud console 

create a VM using gcloud SDK

### Machine types

Machine family and series

![Screenshot 2023-09-10 at 12.18.33 AM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/6104942f-ef63-4d22-8590-3ff7e61b863c/7fb98544-6579-495c-b59a-28ad79e8627e/Screenshot_2023-09-10_at_12.18.33_AM.png)

### Images

Use operating system images to create boot disks for your instances. You can use one of the following image types:

- `Public images` are provided and maintained by Google, open-source communities, and third-party vendors. By default, all Google Cloud projects have access to these images and can use them to create instances.
- `Custom images` are available only to your Google Cloud project. You can create a custom image from boot disks and other images. Then, use the custom image to create an instance.

You can use most public images at no additional cost, but there are some premium images that do add additional cost to your instances. Custom images that you import to Compute Engine add no cost to your instances, but do incur an `image storage charge` while you keep your custom image in your project.

```bash
gcloud compute images list
```

**Machine images**

A machine image is a Compute Engine resource that stores all the configuration, metadata, permissions, and data from multiple disks of a virtual machine (VM) instance. You can use a machine image in many system maintenance, backup and recovery, and instance cloning scenarios.

![Screenshot 2023-09-10 at 1.17.57 AM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/6104942f-ef63-4d22-8590-3ff7e61b863c/a101cacc-4faf-4dd3-acd0-4d23c6e65dae/Screenshot_2023-09-10_at_1.17.57_AM.png)

### External vs. Internal IP Addresses

- `External (Public)` IP addresses are Internet addressable. Resources with external IP addresses can communicate with the public internet.
- `Internal (Private)` IP addresses are internal to a corporate network, Internal IP addresses cannot be reached from the internet
- You CAN NOT have two resources with the same public (External) IP
address.
    - HOWEVER, two different corporate networks CAN have resources with the same Internal
    (private) IP address
- All VM instances are assigned at least one Internal IP address
- Creation of External IP addresses can be enabled for VM instances
    - (Remember) When you `stop` a VM instance, the External IP address is lost

**Static IP Addresses**

https://cloud.google.com/compute/docs/ip-addresses/reserve-static-external-ip-address

`External IP addresses` can be static or ephemeral. If a VM requires a fixed external IP address that `does not change`, you can obtain a static external IP address. You can `reserve new external IP addresses` or promote existing ephemeral external IP addresses.

- Static IP can be switched to another VM instance in the same project
- Static IP remains attached even if you stop the instance. You have to manually detach it.
- Remember: You are `billed` for a Static IP when you
are `NOT using it!`
    - Make sure that you explicitly release a Static IP when you are
    not using it.

## COMPUTE ENGINE - EXAM GUIDE
1.  Planning and configuring compute resources. Considerations include:
    - Selecting appropriate compute choices for a given workload (e.g., Compute Engine, Google Kubernetes Engine, Cloud Run, Cloud Functions)
    - Using preemptible (SPOT) VMs and custom machine types as appropriate
2. Deploying and implementing Compute Engine resources. Tasks include:
    - Launching a compute instance using the Google Cloud console and Cloud SDK (gcloud) (e.g., assign disks, availability policy, SSH keys)
    - Creating an autoscaled managed instance group (MIG) using an instance template
    - Generating/uploading a custom SSH key for instances
    - Installing and configuring the Cloud Monitoring and Logging Agent
    - Assessing compute quotas and requesting increases
    - Launching a Compute Engine instance with custom network configuration (e.g., internal-only IP address, Google private access, static external and private IP address, network tags)
3. Managing Compute Engine resources. Tasks include:
    - Managing a single VM instance (e.g., start, stop, edit configuration, or delete an instance)
    - Remotely connecting to the instance (SSH)
    - Attaching a GPU to a new instance and installing necessary dependencies
    - Viewing current running VM inventory (instance IDs, details)
    - Working with snapshots (e.g., create a snapshot from a VM, view snapshots, delete a snapshot)
    - Working with images (e.g., create an image from a VM or a snapshot, view images, delete an image)
    - Working with instance groups (e.g., set autoscaling parameters, assign instance template, create an instance template, remove instance group)
    - Working with management interfaces (e.g., Google Cloud console, Cloud Shell, Cloud SDK)

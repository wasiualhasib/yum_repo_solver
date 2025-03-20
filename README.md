

# CentOS 8: Failed to download metadata for repo 'appstream'

### CentOS Linux 8 had reached the End Of Life (EOL) on December 31st, 2021. It means that CentOS 8 will no longer receive development resources from the official CentOS project. After Dec 31st, 2021, if you need to update your CentOS, you need to change the mirrors to vault.centos.org where they will be archived permanently.

#### Step 1: Go to the /etc/yum.repos.d/ directory.

#### Step 2: Run the below commands
```
sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```
#### Step 3: To clean all cached information, use the following command
yum clean all

#### Step 4: Now run the yum update

```
yum update -y
```
# CentOS 8: Failed to install perl-IPC-Run package for postgres devel

```
[root@osboxes yum.repos.d]# dnf install perl-IPC-Run -y
Last metadata expiration check: 0:06:17 ago on Thu 20 Mar 2025 04:41:51 PM EDT.
No match for argument: perl-IPC-Run
Error: Unable to find a match: perl-IPC-Run
```
1️⃣ Enable EPEL and PowerTools Repositories
Try enabling the required repositories first:


```
dnf install epel-release -y
dnf config-manager --set-enabled crb
dnf install perl-IPC-Run -y
```

2️⃣ Check for Available Packages
If the above fails, check if the package exists in your repositories:
```
dnf list available | grep perl-IPC-Run
```


# bot
Installing Docker on Windows Server isn’t the same as on Windows 10/11—there’s no Docker Desktop. You install Docker Engine (Mirantis Container Runtime) or use Windows Containers via PowerShell.

Here’s the straightforward way 👇

✅ 1. Check Requirements
Windows Server 2016, 2019, or 2022
Admin privileges
Internet access
🧱 2. Install Containers Feature

Open PowerShell as Administrator and run:

Install-WindowsFeature -Name containers

Restart after installation:

Restart-Computer
📦 3. Install Docker Engine (via PowerShell)

Run this script to install Docker:

Invoke-WebRequest -UseBasicParsing "https://raw.githubusercontent.com/microsoft/Windows-Containers/Main/helpful_tools/Install-DockerCE/install-docker-ce.ps1" -OutFile install-docker-ce.ps1

.\install-docker-ce.ps1

Restart again if prompted.

▶️ 4. Verify Installation

After reboot, check Docker:

docker version

Run a test container:

docker run hello-world:nanoserver
🔧 5. (Optional) Switch Container Mode

Windows Server supports Windows containers only (not Linux containers natively unless using WSL2/Hyper-V setups).

⚠️ Important Notes
No GUI like Docker Desktop
Uses Windows container images (e.g., nanoserver, servercore)
For Linux containers → you’ll need:
Hyper-V VM, or
WSL2 (limited support on Server)
🧠 Alternative (Enterprise Setup)

Instead of Docker CE, Microsoft now supports:

Mirantis Container Runtime (MCR) (paid/support version)
🧪 Example: Run IIS Container
docker run -d -p 80:80 mcr.microsoft.com/windows/servercore/iis
🚀 Quick Summary
Enable Containers feature
Install Docker via script
Restart
Run docker version

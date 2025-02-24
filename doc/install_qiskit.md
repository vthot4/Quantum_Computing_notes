# Install Qiskit

- **Reference:** https://medium.com/@harini.hapuarachchi/a-beginners-guide-to-qiskit-1-0-c8e3e854d732 


## Linux (Ubuntu)

```bash
#!/bin/bash

# Update the package list from the system repository
sudo apt update

# Install updates, patches, etc.
sudo apt upgrade -y

# Check if Python 3 is installed
python3 -V
if [ $? -ne 0 ]; then
    echo "Python 3 is not installed. Installing Python 3..."
    sudo apt install python3-pip -y
fi

# Create a virtual environment
python3 -m venv q2025

# Activate the virtual environment
source q2025/bin/activate

# Install Qiskit and other necessary packages
pip install qiskit
pip install qiskit_ibm_runtime
pip install qiskit[visualization]
pip install jupyter
pip install qiskit_aer
pip install matplotlib
pip install pylatexenc
pip install qiskit-transpiler-service

echo "Installation completed."

```
Save this script in a file called install_qiskit.sh and make sure to give it execution permissions:

```bash
chmod +x install_qiskit.sh
./install_qiskit.sh 
```

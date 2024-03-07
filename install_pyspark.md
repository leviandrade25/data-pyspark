# Install Ubunto from you Microsoft Store
![UBUNTO](images/ubunto.png)

# After Install Ubunto
At this point you may need to update the wsl (Windows system for linux). If that is the case, go to [WSL](https://aka.ms/wsl2kernel) and click in "Linux kernel update package for WSL2 for x64 computers". Run the installation program and go to next step. 

![WSL_UPDATE](images/wsl_update.png)

# You may need..
You may need set the most recent WSL version on your machine.
- Open your CMD
- Run: wsl --unregister Ubuntu
- Open Ubunto again, and it will be reinstalled.
- Define your username (save this info)
- Define your password (save this info)
- Type your password again.
- Installation should return successfully

# Update Ubunto dependencies
On Ubunto Run:
- sudo apt update
- sudo apt -y upgrade

# Install java
On Ubunto run:
- sudo apt install curl mlocate default-jdk -y

# Download Pyspark 
- Go to [Pyspark Download page](https://spark.apache.org/downloads.html)
- Click the link on "Download Spark"
- Copy the URL above the "We suggest the following location for your download:"
- Run wget and the URL you just copied on Ubunto (wget https://dlcdn.apache.org/spark/spark-3.5.1/spark-3.5.1-bin-hadoop3.tgz)
- Run tar xvf spark-3.5.1-bin-hadoop3.tgz to unpack (the file name may be different depending the version you choose)
- For the sake of good practices run sudo mv spark-3.5.1-bin-hadoop3 /opt/spark
- [!Link_pyspark](images/spark_link.png)

# Setting env variables
We need to set the system variables properly for be able to run pyspark command, wherever folder you are in Ubunto.
Run:
- echo "export SPARK_HOME=/opt/spark" >> ~/.profile
- echo "export PATH=$PATH:/opt/spark/bin:/opt/spark/sbin" >> ~/.profile
- echo "export PYSPARK_PYTHON=/usr/bin/python3" >> ~/.profile
- source ~/.profile

# You may fix...
You may find the below error, and need to fix it.
Run:
- vi ~/.profile
- put quotes surrounding PATH variable
- save the alteration with esc :wq!
- [!PATH_VAR](images/path.png)

# Start your cluster
After all these steps you need to run some scripts to run you work and master (letter you'll discuss this)
run:
- sudo /opt/spark/sbin/start-master.sh (will ask you password set at the beginning)
- sudo /opt/spark/sbin/start-worker.sh spark://localhost:7077

# Stop your cluster
It's good to stop the spark local server when you not intent to use it.
Run:
- sudo /opt/spark/sbin/stop-all.sh
# Udacity Full Stack Web Developer Nanodegree Project:
# Linux Server Project

This is a [WSGI](https://www.fullstackpython.com/wsgi-servers.html) catalogue web application that is deployed onto a remote Linux server, which is the third and final project for Udacity's [Full Stack Web Developer Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd0044).

Its primary requirements are:
> 1. User management:  a `grader` user with [sudo](https://linuxhint.com/sudo_linux/) privileges is created & remote `root` access is disabled.
> 2. Firewall: a firewall is configured for security purposes to limit ports used and enforce the use of [SSH](https://www.ssh.com/ssh/protocol) keys.
> 3. App Functionality: configurations of the server are made to serve as a WSGI app & of a database to serve data.
> 4. Documentation: this README file, including the above mentioned and third party resources used for assistance.

## Server & Configuration

IP address: `http://52.0.51.48`
URL: `http://ec2-52-0-51-48.compute-1.amazonaws.com/`
Port: `2200`

### Amazon Web Services Lightsail Server Configuration

#### I. Create Lightsail Instance
1. Create a new AWS account or log in at [Amazon Lightsail](https://lightsail.aws.amazon.com/).
2. Once logged in, click the **Create an instance!** link.
3. Choose **OS Only** instance image of Ubuntu 16.04 LTS.
4. You'll be prompted for an instance plan.  For this project, the lowest one with free-tier access is sufficient.
5. Choose a unique hostname for your image and click the **Create** button.
6. After your instance is "running", click on the **Connect using SSH** orange button.
7. Voilà. You'll then be connected as the default `ubuntu` user.

Source:  [AWS Documentation: Getting Started](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/getting-started-with-amazon-lightsail)

#### II. Create public Static IP
1. Return to the Lightsail console home page.
2. Select **Networking** and then click **Create static IP**.
3. Select the AWS Region of your Lightsail instance.
4. Choose the Lightsail instance you have just created to attach to the static IP.
5. Choose a name for your static IP as instructed.
6.  Finally, select **Create** and you will have just created a static IP for your instance.  The static IP will be necessary for set up with PuTTY.

Source: [AWS Documentation: Static IP](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/lightsail-create-static-ip)

#### III. Lightsail Firewall Settings
1. Go to the **Networking** tab of your instance's management page.
2. Under **Firewall**, click **Add another** to add open ports.
3. Add both ports `123` and `2200` with a `Custom` application & `TCP` protocol.
4.  Click **Save**

Source: [AWS Documentation: Firewall Settings](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/understanding-firewall-and-port-mappings-in-amazon-lightsail)

### PuTTY Download and Configuration (for Windows)

#### I. Download PuTTY & Prepare your Private Key
1. Download the PuTTY installer from its official [website](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
2. Go back to your [Lightsail Console](https://lightsail.aws.amazon.com/).
3. Select **Account** from the top navigation bar & click **Account** from the drop-down.
4. Select the **SSH Keys** tab & click **Download** for the default AWS Region of your instance.
5. Save the `.pem` key file.

#### II. Configure your Lightsail Private Key with PuTTY
1. PuTTY can be set up utilizing the PuTTY Key Generator (PuTTYgen) so start PuTTYgen from your Start menu.
2. Select Load & then the option to show all files.
3. Click **Save private key** & choose to save it with a passphrase or not according to preference.
4. Choose a name and location to store the private key and click **Save**. This will generate a `.ppk` key file.
5. Close PuTTYgen.

#### III. Complete PuTTY configuration with private key and instance details
1. Open PuTTY.
2. Get your static public IP address from Lightsail.
3. Enter the public static IP address in the **Host Name** field & type in the **Port** field `2200`.
4. In **Category** section, expand **SSH** & click **Auth**.
![PuTTY Configuration image](https://d9yljz1nd5001.cloudfront.net/en_us/a1c4e3b2c3818bd57f0175a258b288f0/images/putty-configuration-connection-ssh-auth.png)
5. Click **Browse** to get the `.ppk` key file you created with PuTTYgen & then click **Open**.
6. Make sure to save the session for future use under **Session** as `ubuntu`.
6. Click **Open** once more, & then select **Yes** to trust the connection for future use.
7. Log in under the default user name for Ubuntu: `ubuntu`.
8. You are now logged in and ready to configure from the command line.

Source: [AWS Documentation: Connecting with SSH using PuTTY](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/lightsail-how-to-set-up-putty-to-connect-using-ssh)

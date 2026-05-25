<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This project outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. It includes configuring IIS, PHP, MySQL, and integrating all components to support a fully functional ticketing system.<br />


You can find all the necessary installation files for this project below:  
[Download Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)




<h2>Environments and Technologies Used</h2>

<p align="left">
<img src="https://skillicons.dev/icons?i=azure,windows,php,mysql" />&nbsp;&nbsp;


- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- PHP
- MySQL
- osTicketing

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure Subscription 
- Azure Virtual Machine
  - OS: Windows 10
  - vCPUs: 2
- Remote Desktop Connection


<h2>Installation Steps</h2>

### Step 1: Create and Configure the Azure Virtual Machine

Once logged into the Microsoft Azure Portal, deploy a Virtual Machine using the following configuration.

- OS: Windows 10 Pro 2
- VM Name and Resource Group: osticket-vm / osticket
- vCPUs: 2
- Credentials: Username/Password (As you please)
- Remote Desktop Client

Once the Virtual Machine is deployed, you can securely connect to the VM by obtaining the public IP address of the VM, followed by using Remote Desktop Connection with the created credentials to begin configuration. 
<img width="1919" height="957" alt="Screenshot 2026-05-25 155702" src="https://github.com/user-attachments/assets/a125df55-172a-498c-8479-b35cd31014c8" />
> [!NOTE]
> All of the following downloadable files are attached together and can be found at the top of the page.

### Step 2: Install and Configure within Virtual Machine 
Within the `osticket-vm` environment, the osTicket installation package was downloaded and extracted to the desktop to prepare the required installation dependencies.

<img width="630" height="453" alt="Screenshot 2026-05-25 163637" src="https://github.com/user-attachments/assets/054c35e4-e573-4566-8a1e-701ee3502474" />
<img width="442" height="231" alt="Screenshot 2026-05-25 163629" src="https://github.com/user-attachments/assets/e32efb4e-9105-4938-bd6e-7e587434f75a" />

### Step 3: Install and Enable IIS with CGI 
Configured the Windows web server environment by enabling Internet Information Services (IIS) through the Windows Features settings in the Control Panel. Additionally, CGI was enabled under World Wide Web Services → Application Development Features to support PHP functionality required for the osTicket installation.
<img width="687" height="393" alt="Screenshot 2026-05-25 164644" src="https://github.com/user-attachments/assets/44892dca-cba8-419b-9da4-826e970e6dcf" />

### Step 4: Install Required Components
Installed PHP Manager for IIS (`PHPManagerForIIS_V1.5.0.msi`) from the `osTicket-Installation-Files` directory to enable PHP configuration management within IIS.

<img width="1025" height="576" alt="Screenshot 2026-05-25 165339" src="https://github.com/user-attachments/assets/0d341fdc-a7b4-460c-b30e-d33f04dd2ebf" />

Installed the IIS URL Rewrite Module (`rewrite_amd64_en-US.msi`) from the installation files directory to support URL rewriting functionality required for the osTicket environment.

<img width="1023" height="572" alt="Screenshot 2026-05-25 165738" src="https://github.com/user-attachments/assets/9f1e227d-40b1-4355-bdfa-3ebe40a79c3d" />

### 4.1: Setup PHP 

Created a dedicated `C:\PHP` directory within the Windows environment and extracted the PHP application files into the directory to support the osTicket installation requirements.

<img width="558" height="409" alt="Screenshot 2026-05-25 171255" src="https://github.com/user-attachments/assets/ca112976-40d8-4596-b106-77e9f6dd72f4" />

<img width="1024" height="572" alt="Screenshot 2026-05-25 171141" src="https://github.com/user-attachments/assets/aadf34c6-60cb-4b40-9708-bf7b1f146758" />

Installed the Microsoft Visual C++ Redistributable package (`VC_redist.x86.exe`) from the `osTicket-Installation-Files` directory to provide the required runtime dependencies for the osTicket environment.

<img width="791" height="574" alt="Screenshot 2026-05-25 171940" src="https://github.com/user-attachments/assets/e2246a5e-2717-4463-a5e4-95fa44fe0ab8" />

Installed MySQL Server 5.5.62 (`mysql-5.5.62-win32.msi`) using the Typical Setup configuration. After installation, the MySQL Configuration Wizard was launched and configured using the Standard Configuration option. The MySQL root account was configured with the username `root` and password `root`.

<img width="789" height="576" alt="Screenshot 2026-05-25 172055" src="https://github.com/user-attachments/assets/461c7f89-35b2-49c2-8234-f4d5cdb3b613" />
<img width="448" height="349" alt="Screenshot 2026-05-25 172017" src="https://github.com/user-attachments/assets/25624aae-7aaf-41b9-a95d-0dab73547abe" />
<img width="455" height="342" alt="Screenshot 2026-05-25 172151" src="https://github.com/user-attachments/assets/0be99efb-315b-419e-86df-26d122c9b939" />
<img width="456" height="347" alt="Screenshot 2026-05-25 172228" src="https://github.com/user-attachments/assets/0cea798a-8858-4bbc-91d8-a4a6dc29c67e" />

### Step 5: Configure IIS

Opened Internet Information Services (IIS) as adminstrator and registered PHP within IIS using PHP Manager by linking the `php-cgi.exe` executable located in the `C:\PHP` directory.
<img width="715" height="321" alt="Screenshot 2026-05-25 175139" src="https://github.com/user-attachments/assets/f44fb1f4-35ea-4e75-8904-7b33afbe1be4" />
<img width="843" height="357" alt="Screenshot 2026-05-25 175227" src="https://github.com/user-attachments/assets/902d7be3-7e9b-4c58-a908-e6f83aee9073" />
<img width="861" height="259" alt="Screenshot 2026-05-25 175306" src="https://github.com/user-attachments/assets/483ab9ea-7558-4308-9a69-4aebb5103abf" />

### Step 6: Installing osTicketing

Extracted the `osTicket-v1.15.8.zip` installation package from the `osTicket-Installation-Files` directory and transferred the `upload` folder into the `C:\inetpub\wwwroot` web server directory.
<img width="792" height="575" alt="Screenshot 2026-05-25 180132" src="https://github.com/user-attachments/assets/0f7cb2e0-e490-4fca-902f-cf119ccd3c34" />

<img width="1045" height="590" alt="Screenshot 2026-05-25 180307" src="https://github.com/user-attachments/assets/8507b40e-ac7f-4c9a-b24c-278ea4cf3659" />

Renamed the `upload` directory to `osTicket` within `C:\inetpub\wwwroot` to prepare the application directory structure for deployment through IIS.

<img width="492" height="262" alt="Screenshot 2026-05-25 180332" src="https://github.com/user-attachments/assets/4ac1a74a-6f97-4787-9d8f-4abead45301a" />

Restarted IIS services by stopping and starting the web server within IIS Manager to apply the osTicket deployment changes.

<img width="234" height="196" alt="Screenshot 2026-05-25 180415" src="https://github.com/user-attachments/assets/2c8aa9bb-5c03-41af-85a3-3b1dc8b46ea2" />

Navigated to `Sites → Default Web Site → osTicket` within IIS Manager and launched the application using the `Browse *:80` option to verify web accessibility.
<img width="1068" height="311" alt="Screenshot 2026-05-25 180509" src="https://github.com/user-attachments/assets/e7cbe9dd-fb5e-4f91-8890-706e447d57c8" />

During the initial osTicket setup validation, several required PHP extensions were identified as disabled. Accessed PHP Manager within the osTicket site configuration and enabled the following PHP extensions to satisfy application requirements:

<img width="316" height="153" alt="Screenshot 2026-05-25 180559" src="https://github.com/user-attachments/assets/7459a192-2ca6-4a93-83df-dfb6b88c2431" />
<img width="1067" height="409" alt="Screenshot 2026-05-25 180550" src="https://github.com/user-attachments/assets/55089ee2-cf70-47fe-9e39-c9a113399179" />

Accessed the PHP Manager extension configuration settings within IIS and enabled the required PHP modules necessary for osTicket functionality, including `php_imap.dll`, `php_intl.dll`, and `php_opcache.dll`.
<img width="1075" height="679" alt="Screenshot 2026-05-25 181706" src="https://github.com/user-attachments/assets/fd69c1fb-faac-4510-96b9-6ca179886e31" />

### Step 7: Configure osTicket
Renamed the `ost-sampleconfig.php` configuration file to `ost-config.php` within the `C:\inetpub\wwwroot\osTicket\include` directory to initialize the primary configuration file required for the osTicket setup process.

<img width="205" height="146" alt="Screenshot 2026-05-25 182148" src="https://github.com/user-attachments/assets/f7a1a9ec-c8ba-46ab-8bbd-24e80d1534d7" />
<img width="561" height="406" alt="Screenshot 2026-05-25 182142" src="https://github.com/user-attachments/assets/31f59aa5-a208-487c-b3b7-88044b3420b9" />


Modified the security permissions for the `ost-config.php` file by disabling inherited permissions and removing existing access entries. Configured a new permission rule granting full control access to the `Everyone` group to allow osTicket to complete the web-based configuration process.

<img width="477" height="306" alt="Screenshot 2026-05-25 182332" src="https://github.com/user-attachments/assets/454650ad-d244-4aea-974a-61eebb01b3d9" />

Proceeded with the osTicket browser-based setup wizard and configured the initial help desk settings, including the system help desk name and the default email address used for receiving customer support requests.

<img width="910" height="577" alt="Screenshot 2026-05-25 182700" src="https://github.com/user-attachments/assets/f932f952-7573-4cf2-a7ad-ad90472c7fb1" />

### Step 8: HeidiSQL Setup

Installed HeidiSQL from the `osTicket-Installation-Files` directory to manage the MySQL database environment for the osTicket deployment.

<img width="503" height="252" alt="Screenshot 2026-05-25 182822" src="https://github.com/user-attachments/assets/29e57a5b-eac3-44b9-af47-62cdcc319ef8" />

Launched HeidiSQL and configured a new database session using the MySQL root credentials. Connected to the MySQL instance and created a new database named `osTicket` to support the ticketing system installation.
<img width="622" height="435" alt="Screenshot 2026-05-25 182911" src="https://github.com/user-attachments/assets/a3f8cc17-e9af-479c-9eb4-14ce5969b9af" />
<img width="288" height="233" alt="Screenshot 2026-05-25 183000" src="https://github.com/user-attachments/assets/7b79d907-b64b-4dff-b6e3-267a5bf4c490" /> 
<img width="423" height="348" alt="Screenshot 2026-05-25 182945" src="https://github.com/user-attachments/assets/36941122-9c11-4f8b-a074-7ace63d8d302" />

### Step 9: Finalize and Complete osTicket Setup

Finalized the osTicket installation within the browser by configuring the MySQL database connection settings, including the `osTicket` database and MySQL root account credentials.
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: root
- Click Install Now
<img width="748" height="296" alt="Screenshot 2026-05-25 183108" src="https://github.com/user-attachments/assets/91ba570c-c37d-4bb8-8b0c-949a7b1ec798" />

<img width="747" height="580" alt="Screenshot 2026-05-25 184009" src="https://github.com/user-attachments/assets/09954e8c-c0da-4698-ab04-ffca5b8e2825" />


### Step 10: Accessing osTicketing
- Admin Panel: http://localhost/osTicket/scp/login.php
- End-User Portal: http://localhost/osTicket/

## Conclusion 
Successfully deployed and configured the osTicket help desk environment within a Windows virtual machine using IIS, PHP, and MySQL. This project provided hands-on experience with web server configuration, database setup, application deployment, and ticketing system management within a simulated IT support environment.







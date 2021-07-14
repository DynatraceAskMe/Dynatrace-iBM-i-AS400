# Dynatrace-iBM-i-AS400
How to monitor IBM i ( AS400 )using the IBM i ActiveGate extension.  
## Prerequisites  
1.  Dynatrace 1.170+ 
2.  ActiveGate 1.170+  
    - ActiveGate version 1.175+ is ready to accept and run extensions. If you are running an earlier version of ActiveGate,   
      see [Install ActiveGate plugin module](https://www.dynatrace.com/support/help/extend-dynatrace/extensions/development/install-activegate-plugin-module/) for instructions on installing the plugin module.  
    - For Environment ActiveGate installation instructions, see [Dynatrace ActiveGate](https://www.dynatrace.com/support/help/extend-dynatrace/extensions/development/install-activegate-plugin-module/).  
    - How to [Install environment ActiveGate](https://github.com/DynatraceAskMe/Install-Dynatrace-ActiveGate-On-Linux/blob/main/README.md)  
3.  IBM i (formerly iSeries/ AS400) 7.2+ host. 
4.  An ODBC driver manager installed on your ActiveGate host. 
5.  DB2 for i ODBC driver installed on the ActiveGate. 
6.  Open ports between ActiveGate and IBM i server:  

    [![Screen-Shot-2564-07-13-at-17-41-56.png](https://i.postimg.cc/2yXh5NFv/Screen-Shot-2564-07-13-at-17-41-56.png)](https://postimg.cc/Wqgh9Kyb)  
    
## ODBC driver manager installation (Linux only)
If your ActiveGate host is running on Linux, install the unixODBC driver manager according to your environment:  

RedHet:  
>yum install unixODBC 

Ubuntu:  
>apt-get install unixodbc-dev unixodbc-bin unixodbc  


## DB2 for i ODBC driver
iBM provides an ODBC driver for Windows or Linux  applications to connect to IBM i, You can download ODBC driver packages from [IBM’s ESS](https://www.ibm.com/support/pages/obtaining-ibm-i-access-client-solutions) site.  

## Extension Installation  
1.  Download IBM iSeries ActiveGate extension, You can download IBM iSeries ActiveGate extension from [iBM i](https://www.dynatrace.com/hub/?query=iBM)  
2.  Download to get the extension ZIP file. Don't rename the file.  
3.  Unzip the ZIP file to the **plugin_deployment** directory of your ActiveGate host.
    #### ActiveGate on Windows  
    You can deploy extension the ActiveGate deployment directory. By default **%PROGRAMFILES%\dynatrace\remotepluginmodule\plugin_deployment**  

    [![message-Image-1626171461603.jpg](https://i.postimg.cc/NGCwtGrM/message-Image-1626171461603.jpg)](https://postimg.cc/Z0NQFSHt)
    
    #### ActiveGate on Linux    
    You can deploy extension the ActiveGate deployment directory. By default **%/opt/dynatrace/remotepluginmodule/plugin_deployment**  
    
    [![Screen-Shot-2564-07-13-at-22-28-34.png](https://i.postimg.cc/bv4cM67Y/Screen-Shot-2564-07-13-at-22-28-34.png)](https://postimg.cc/qtc56GBW)
    
4.  Install ODBC driver packages (iBm i) on your ActiveGate host.  

    [![Screen-Shot-2564-07-13-at-22-50-38.png](https://i.postimg.cc/nz7NCg2s/Screen-Shot-2564-07-13-at-22-50-38.png)](https://postimg.cc/1nmvdWLP)  
    
5.  Install ODBC driver packages (iBm i) on your ActiveGate host.  
6.  Restart Dynatrace RemotePluginModule service.  
    
    - On Linux, restart the service using the following commands with admin rights:  
        >systemctl restart remotepluginmodule.service  
       
    - On Windows, run these two commands in a Command Prompt launched as Admin:  
        >sc stop "Dynatrace Remote Plugin Module"  
        >sc start "Dynatrace Remote Plugin Module"  


8.  In Dynatrace, select **Settings**, the **Monitoring** button, **Monitored technologies**, **Custom extensions**,**Upload extensions**, and upload the zipped file used in step 2.  

    [![message-Image-1626171473046.jpg](https://i.postimg.cc/pTxk3jBS/message-Image-1626171473046.jpg)](https://postimg.cc/3ySgvdVj)
    
    [![message-Image-1626171483248.jpg](https://i.postimg.cc/ydkhMTZv/message-Image-1626171483248.jpg)](https://postimg.cc/CBpfDkJq)
    
8.  After, you upload extension successful, you can click the **iBM i (Version ...)**  
    
    [![message-Image-1626171492474.jpg](https://i.postimg.cc/J7jKMPF2/message-Image-1626171492474.jpg)](https://postimg.cc/z3XTkS8C)

9. Enter the endpoint information requested for connecting to the AS400.  
  
    #### For example configuration
    
    [![Screen-Shot-2564-07-13-at-18-29-45.png](https://i.postimg.cc/13dYf4rC/Screen-Shot-2564-07-13-at-18-29-45.png)](https://postimg.cc/nXv1WF5B)  
    You can see endpoint configuration from this [link](https://www.dynatrace.com/support/help/shortlink/ibm-i#extension-installation) 
    
    [![Screen-Shot-2564-07-13-at-16-22-18.png](https://i.postimg.cc/qvK2xRdZ/Screen-Shot-2564-07-13-at-16-22-18.png)](https://postimg.cc/3kKyK3Ng)
    
    
# Reference:
[IBM i monitoring | Dynatrace Documentation](https://www.dynatrace.com/support/help/shortlink/ibm-i)

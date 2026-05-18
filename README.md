# Semanage-port-or-add-port-in-system-
port is a 16-bit numerical identifier (ranging from 0 to 65535) that serves as a logical communication endpoint for network traffic. It allows the operating system to direct incoming data to the correct application or service

* PORT  <br>
  * A port is a logical communication endpoint used by a computer to decide which application should receive network traffic. <br>
  * Think of an IP address as the building address, and a port as the room number inside that building <br>

* Two main protocols use in port
    * TCP :- reliable connection , used by HTTP , SSH , HTTPS
    * UDP :- faster , connectionless , used by DNS , Streaming gaming
  
Example: for adding a port 80 
192.168.1.10 = IP address of the machine <br>
80 = port number <br>
Port (80) usually means a web server using HTTP <br>

Common ports :- 

  20/21  FTP <br>
  22     SSH <br>
  25     SMTP email <br>
  53     DNS <br>
  80     HTTP <br>
  443    HTTPS <br>
  3306   MySQL <br>
  5432   PostgreSQL <br>
  8080   Common web/dev server port <br>


# Adding port 82
 
 #semangage port -l | grep http      <br>
 #semanage port -a -t http_port_t -p tcp 82 <br>
 #firewall-cmd --permanent --add-port=82/tcp <br>
 #firewall-cmd --reload <br>
 #systemctl enable --now httpd.service <br>
 #systemctl restart httpd.service <br>

Information of this command 
 * #semanage port -l | grep http <br>
 semanage port is command for port adding , deleting etc., and -l used for finding all port in system then grep is used for find specific word in this we find http

 * #semanage port -a -t http_port_t -p tcp 82 <br>
 this command is used for adding port in system  then 
   * semanage port (manage SELinux port)
   * -a (add a new port)
   * -t http_port_t (assign the SELinux type http_port_t)
   * -p tcp (the port uses the tcp protocol)
     
 * #firewall-cmd --permanent --add-port=82/tcp 
   The command is meant to permanently open a firewall port 
     * firewall-cmd = command-line tool for managing firewalld 
     * --permanent = save the rule permanently, so it remains after reboot 
     * --add-port=82/tcp = open port 82 using the TCP protocol

  * firewall-cmd --reload
   This command reloads firewalld rules

     * firewall-cmd = command-line tool for managing the Linux firewall service firewalld
     * --reload = reload firewall configuration files and apply permanent changes

 * #systemctl enable --now httpd.service
   This command does two things at once for the Apache web server service.

    * systemctl = command used to manage systemd services
    * enable = make the service start automatically at boot
    * --now = start the service immediately right now
    * httpd.service = Apache HTTP Server service name on RHEL/CentOS/Fedora
      


  



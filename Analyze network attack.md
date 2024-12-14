# Cybersecurity Incident Report: Analyze Network Attacks
> Network attacks.

> Please visit this [link](https://www.coursera.org/learn/networks-and-network-security?specialization=google-cybersecurity) for further information. 

## Scenario

Here, I worked as a security analyst for a fictituous travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, I received an automated alert from my monitoring system indicating a problem with the web server. I attempted to visit the company’s website, but I received a connection timeout error message in my browser.

I then used a packet sniffer to capture data packets in transit to and from the web server. I noticed a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. I suspect the server is under attack by a malicious actor. 

I took the server offline temporarily so that the machine can recover and return to a normal operating status. I also configured the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. I know that my IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. I needed to alert my manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. I needed to be prepared to tell my boss about the type of attack I discovered and how it was affecting the web server and employees.

## Type of Attack That May Have Caused This Network Interruption 

* One potential explanation for the website's connection timeout error message is: DOS attack <br>
* The logs show that: Web server stops responding after receiving so many SYN packet requests <br>
* This event could be: Syn flood attack

## How the Attack is Causing the Website Malfunction 
When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol: 

| Step | Description |
|---|---|
| 1 | `SYN` : Client sends SYN packet to the server, requesting a connection. |
| 2 | `SYN/ACK` : Server responds with SYN/ACK packet, acknowledging the client's SYN and requesting confirmation of the connection. |
| 3 | `ACK` : Client sends ACK packet to the server, acknowledging the server's SYN/ACK. |

* What happens when a malicious actor sends a large number of SYN packets all at once: It slows down the traffic to the point where such request will fail to be executed. It overwhelms the server’s available resources to reserve for the connection. When this happens, there are no server resources left for legitimate TCP connection requests. <br>
* What the logs indicate and how that affects the server: The server has become overloaded and unable to receive any more visitors. In addition, those new visitors will receive a connection timeout message. 

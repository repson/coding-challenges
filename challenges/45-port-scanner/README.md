Coding Challenge #45 - Port Scanner
This challenge is to build your own version of a port scanner like nmap.
John Crickett
Jan 20, 2024

Hi this is John with this week’s Coding Challenge.

🙏 Thank you for being one of the 39,182 software developers who have subscribed, I’m honoured to have you as a reader. 🎉

If there is a Coding Challenge you’d like to see, please let me know by replying to this email. 📧

Coding Challenge #45 - Build Your Own Port Scanner

This challenge is to build your own version of a port scanner like nmap.

A port scanner is an program that probes a host to identify open network ports. Bad actors use port scanners to find network services running on a host in order to find and exploit vulnerabilities. Security analysts and network administrators use port scanners to confirm network security policies are being complied with.

Nmap (short for Network Mapper) is probably the most widely used port scanner. It is a free open source tool written in C. You can find the source in the Nmap GitHub repo if you’re interested in digging into it.
If You Enjoy Coding Challenges Here Are Four Ways You Can Help Support It

    Refer a friend or colleague to the newsletter. 🙏

    Sign up for a paid subscription - think of it as buying me a coffee ☕️ twice a month, with the bonus that you also get 20% off any of my courses.

    Buy one of my courses that walk you through a Coding Challenge.

    If you work for a company that sells to software engineers, encourage them to sponsor the newsletter. 🙏

    Refer a friend

The Challenge - Building A Network Port Scanner

In this challenge we’re going to build a command line tool to scan a network or range of host looking for open ports.

How a Port Scanner Works

Running a port scan on a network or server reveals which ports are open and listening as well as revealing the presence of devices, such as firewalls.

Port scanning is a valuable technique for both testing network security and the strength of the system’s firewall. For the same reason it is also a popular starting point for bad actors seeking a point of access to break into a network or server.

Ports vary in their services offered. They are numbered from 0 to 65535, but certain ranges are more frequently used. Ports 0 to 1023 are identified as the “well-known ports” and have been assigned services by the Internet Assigned Numbers Authority (IANA). Some of the most prominent ports and their assigned services include:

    Port 20 (UDP) — File Transfer Protocol (FTP).

    Port 22 (TCP) — Secure Shell (SSH).

    Port 23 (TCP) — Telnet protocol - usually not available these days due to it being unencrypted and therefore unsecure.

    Port 53 (UDP) — Domain Name System (DNS).

    Port 80 (TCP) — HTTP.

    Port 443 (TCP) — HTTPS.

There are standard services offered on ports above 1023 too - for example, as we saw in the build your own Redis challenge, the default Redis port is 6379.

There are other ports that, if open, may indicate a system that has been compromised. Thus a port scanner can be an incredibly useful tool for system administrators, security engineers and anyone responsible for securing a network.

Step Zero

As always, before we tackle Step 1 of the Coding Challenge, you’re going to set your environment up ready to begin developing and testing your solution.

I’ll leave you to choose your target platform, setup your editor and programming language of choice. I’d encourage you to pick a tech stack that you’re comfortable doing network programming with - we’re building a network tool after all! 😀

‼️WARNING - Only run a port scanner against a host that you have permission to scan‼️

✅ The good folks behind Nmap provide a public host you can scan, please read and respect their fair usage policy, details here: http://scanme.nmap.org/

Step 1

In this step your goal is to create a CLI program that will accept two command line arguments:

    A host

    A port

It will then try to open a TCP connection to the port and will report back if the port is open. For example if you have a service running locally on port 5000 and you run you port scanner it should look something like this:

% ccscan -host=localhost -port=5000
Scanning host: localhost port: 5000
Port: 5000 is open

If a port is open you’ll be able to make a full TCP connection to it.

Step 2

In this step your goal is to expand this to what is known as a vanilla scan. A vanilla scan is the most basic scan offered by a port scanner, it will attempt to open a full TCP connection to each of the 65,535 ports on a server. A port number is a 16-bit unsigned integer, so there are theoretically 65536 ports, but 0 is reserved, so we don’t use it.

Running this step should look something like this:

% ccscan -host=localhost
Scanning host: localhost 
Port: 5000 is open
Port: 8080 is open

In this case only ports 5000 and 8080 are open on my laptop. If you’re curious those ports are open because I’m working on a course on how to build your own Load Balancer in Go, my backend server is running on 5000 and the test load balancer is on 8080.

Step 3

Unless you read ahead, or thought ahead, you probably found that it took quite a while for your port scanner to get through 65k ports. There are two ways around this:

    Reduce the connection timeout - only spend a few hundred milliseconds to a second trying to connect to a port.

    Scan multiple ports in parallel.

In this step your goal is to apply those two changes to your port scanner and have it scan a host as fast as possible. I’d suggest adding the timeout and number of concurrent ports to test as command line options with a reasonable set of defaults.

Step 4

In this step your goal is to implement a sweep scan. A sweep scan tests the same port across a number of host to identify which hosts on a network are active. This allows a user to identify which host on a network are active. It is often used as a preliminary scan to identify targets for a full scan.

For this step you should change your program to support taking either a list of hosts or a wildcard IP address, for example:

% ccscan -host=localhost,192.168.1.10

% ccscan -host-192.168.1.*

You could also extend this to accept the hosts in CIDR notation.

Step 5

All the scans so far have been vanilla scans - creating a full TCP connection allowing the operating system to conduct a full TCP handshake for us. This approach makes it easy for the scans to be detected because firewalls log full TCP connections.

To avoid detection port scanners often run what is known as a SYN scan - also sometimes referred to as a half-open scan (because the connection is never fully opened). To provide some context, here’s the steps in a TCP handshake:

    The client sends an SYN packet which contains a random sequence number A. SYN stands for synchronize.

    The server sends back a SYN-ACK packet. ACK stands for acknowledgment. This packet contains the sequence number A incremented by one and a new random number B.

    The client finishes with an ACK of the server’s response. This packet that contains A + 1 and B + 1.

For a half-open of scan the scanner only send a SYN packet to the port. When it receives the SYN-ACK from the target host it knows the port is open, but it does not then complete the TCP handshake and does not send the ACK.

If the scanner receives a RST packet it knows the port is closed. RST stands for reset. A reset packet means a port will not accept connections or receive more data. If no response is received the host is unreachable (unlikely if a sweep scan identified the host) or being blocked by a firewall.

In this step your goal is to implement a SYN scan. To do this you’ll need to read up on how to send raw network packets on your operating system using your chosen programming language.

Going Further

If you want to take this challenge further take a look at the functionality of Nmap for inspiration. It is a powerful and complete tool, but implementing your own will teach you a lot about low level network protocols and programming as well as network security.
2 Other Ways I Can Help You:

    I write another FREE newsletter Developing Skills that helps you level up the other skills you need to be a great software developer.

    I have some courses available:

        Build Your Own Redis Server (Python Edition) which guides you through solving the Redis Coding Challenge in Python.

        Build Your Own Shell (Go Edition) which guides you through solving the Shell Coding Challenge in Go.

Share Your Solutions!

If you think your solution is an example of the developers can learn from please share it, put it on GitHub, GitLab or elsewhere. Then let me know via Twitter or LinkedIn or just post about it there and tag me.
Request for Feedback

I’m writing these challenges to help you develop your skills as a software engineer based on how I’ve approached my own personal learning and development. What works for me, might not be the best way for you - so if you have suggestions for how I can make these challenges more useful to you and others, please get in touch and let me know. All feedback greatly appreciated.

You can reach me on Twitter, LinkedIn or through SubStack

Thanks and happy coding!

John
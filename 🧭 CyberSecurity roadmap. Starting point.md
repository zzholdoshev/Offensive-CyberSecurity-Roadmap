
> [!CbS roadmap]
>   Series of Cybersecurity roadmaps for those who want to learn offensive security (pentest/reverse engineering). The roadmaps are intended to be viewed in Obsidian. "Starting point" roadmap is intended primarily as starting point for pentest, contains most important things to help you get started with CTF. Only **Free** labs and courses are included in all roadmaps. Combined with intermediate and advanced roadmaps, it can build a solid foundation for offensive security and help you land a job in CbS. OSINT and stegano are not included in this roadmap - these topics can be explored within the challenges on platforms from [[🧭 CyberSecurity roadmap. Starting point#^8af021|links]])

# Suggested Order ([[CbS Roadmap Visualization.canvas|visualization]]): 

1.  Starting point. Go through this roadmap from top to bottom, starting from [[🧭 CyberSecurity roadmap. Starting point#^06e269|Intro]] #basic_cbs #web_I #privesc_I #linux_I #networks_I #CTF #forensics #C #SQL #python #git #gdb 
	 > Start participating in CTFs as early as possible. Find you local [CTF](https://ctftime.org), or/and join HTB CTF [events](https://ctf.hackthebox.com/events/live) ^fb96d5

After completing Starting point, choose specialization:
- [[🏴Pentest roadmap|pentest roadmap]]  #web_II #infra #linux_II #docker #AD #windows #privesc_II #networks_II
	> In order to better understand web apps - try building something. In terms of languages I suggest Go[^1] OR Java or any other language used for backend):
	
	- [ ] backend bootcamp in Ecole 42 / School 21 (**for ecole42/school21 students**)
	- [ ] Go / Java bootcamp in Ecole 42 / School 21 (**for ecole42/school21 students**)

   	> OR an alternative for non-students:
	- [ ] Learn Go or Java:
		* [ ] learn Go (best choice for pentset) - it is best to use official [docs](https://go.dev/doc/) and [interactive course](https://go.dev/tour/welcome/1). [Go by example](https://gobyexample.com). Also review this [course](https://www.w3schools.com/go/index.php)
			`OR:`
		- [ ] [Java](https://java-programming.mooc.fi) (best choice for appsec/reverse/mobile security researcher)
	- [ ] build backend as [pet-project](https://roadmap.sh/golang/projects?difficulty=advanced), or search project ideas in any other language
	> optional:
	* [ ] [[☁️cloud CbS roadmap|cloud CbS roadmap]] - a cloud-oriented roadmap for junior/intern appsec position in cloud. Otherwise skip this step. #cloud #kubernetes 
	> recommended:
	- [ ] [[🧭 CyberSecurity roadmap. Starting point#^45da8d|yandex CbS course(RU)]]

- Vulnerability research roadmap. Solid college-level foundation for CbS on topics like #reverse #binary #system_security #low_level #kernel #sandboxing #programming #code_security #malware^114cf4
	> reverse engineering and binary exploitation
	 * [ ] [pwn.college](https://pwn.college/dojos) -  free comprehensive college-level courses from Arizona State University. Recommended to do every module in getting started and core material. Linux Luminarium, playing with programs, access control, privEsc, crypto are included in the first 2 roadmaps. Do everything that is left there. Basically you need every module that is in CSE365 and CSE466 (getting started and core materials)
		 - [ ] pwn.college getting started dojos
		 - [ ] pwn college core material dojos
	 - [ ] C: 
		 - [ ] security-oriented C [roadmap](https://github.com/h0mbre/Learning-C) . You should know most of the topics if you completed Core from the first roadmap. It makes sense to go through assignment 21-28 .
		 - [ ] C: github roadmap [learn C in 60 days](https://github.com/Sckab/C-RoadMap/tree/master) (take this roadmap if you did school21/ecole42 C bootcamp instead of "alternative" path, covered in this [[🧭 CyberSecurity roadmap. Starting point#^a97ce8|roadmap]]). You can skip the first 3 weeks.
		* [ ] implement some C project ideas in this [roadmap](https://github.com/hoppersroppers/roadmap/blob/master/training/c.md). Recommended the first 2-3 (shell, malloc etc)
	 * [ ] [Nigthmare Remix by roppers](https://github.com/hoppersroppers/nightmare) - solid foundation for reverse / binary exploitation, theory + CTF challenges
	 * [ ] [OverTheWire](https://overthewire.org/wargames/) - leviathan, narnia, behemoth - classic reverse / binary exploitation wargames
	 * [ ] Modern Binary Exploitation [course](https://github.com/RPISEC/MBE) from RPISEC
	 * [ ] ROP [challenges](https://ropemporium.com/) - binary exploitation challenges
	 * [ ] [How2Heap](https://github.com/shellphish/how2heap) - heap exploitation 
	 * [Crackmes](https://crackmes.one) and other [[🧭 CyberSecurity roadmap. Starting point#^8af021|links]]
	
	 > malware courses
	* [ ] https://malwareunicorn.org/workshops/re101.html#0
	* [ ] https://malwareunicorn.org/workshops/re102.html#0
	 
	 > Advanced coding. Learn programming languages like (`C++/rust`[^1]) and OOP. Try building pet projects. There are some courses in russian. If you don't know russian, use AI for translation. 
	 * [ ] C++: great introductory russian-language [course](https://education.yandex.ru/handbook/cpp) from Yandex(RU)
	 * [ ] C++: https://www.learncpp.com 
	 * [ ] OOP C++: [course(OOP C++)](https://stepik.org/course/205781/info). Best course on OOP(RU)
	* C++: check this [roadmap.sh](https://roadmap.sh/cpp). Also you can develop your own roadmap on learning C++ by asking AI, include coding tasks at the end of every topic.
	* rust is optional but recommended:
		 * [ ] Rust: official "[rust book](https://rust-book.cs.brown.edu/title-page.html)", quizes included
		 * [ ] Rust: 30 days of Rust [roadmap](https://github.com/Hunterdii/30-Days-Of-Rust/blob/main/README.md#-30-days-of-rust) - great roadmap
		 * [ ] Rust: russian-language [course](https://stepik.org/course/195449/syllabus)
		 * [ ] Rust bootcamp at Ecole42 (**for ecole42 students**)
	* [ ] implement at least 2-3 pet projects from this [repo](https://github.com/CarterPerez-dev/Cybersecurity-Projects) and review these projects [build-your-own-x](https://github.com/codecrafters-io/build-your-own-x). Recommended: for web/infra pentest - web server, browser, network stack, dns server, for low-level -  docker, shell, emulator
	 * [ ] [Core security from OSSU (OpenSource Society University)](https://github.com/ossu/computer-science?tab=readme-ov-file#core-security) - identifying security vulnerabilities(C++/Java), principles of secure coding #appsec
	* For additional specialization and pivoting look up different CbS specialization roadmaps on github
	> roadmaps:
	 * https://github.com/hoppersroppers/roadmap/blob/master/training/hardstuff.md - reverse
	 * https://github.com/hoppersroppers/roadmap/blob/master/training/pwning.md - binary exploitation
	 * comprehensive [roadmap](https://github.com/x86byte/RE-MA-Roadmap) for reverse engineering and malware analysis
	 * You can also review this [roadmap](https://github.com/hoppersroppers/roadmap/blob/master/README.md). It is partly integrated in this roadmap.
- [[Low-level BugBounty roadmap]]
* Do when you are ready:
	> CbS games & BugBounty (recommended upon completion of [[🏴Pentest roadmap]]): ^718bdd
	* BugBounty: https://bugbounty.standoff365.com/programs/standoff-365?tab=1
	-  VDP
	* https://www.hackerone.com/bug-bounty-programs
	* https://bugbounty.ru/
	* Bootcamp: https://hackbase.standoff365.com/battle/7/industry/27?tab=general
		`A virtual infrastructure with realistic replicas of systems and software from different industries, in which cybersecurity specialists can train 24/7.` 
	* Cyberbattle https://cyberbattle.standoff365.com attack-defense CbS game with cash prize
	* [HacTheBox Fortresses - attack a copy of a real company infra](https://app.hackthebox.com/fortresses) 

# Intro - overview of cybersecurity

^06e269

- [ ] CS50 [CyberSecurity](https://youtube.com/playlist?list=PLhQjrBD2T383Cqo5I1oRrbC1EKRAKGKUE&si=03-zJ1H9ROsNyFsC). An introduction to cybersecurity for technical and non-technical audiences alike. Basic overview. You can skip this if you already know most of the topcs.
# Intro - linux and data encoding
- [ ] install linux as primary desktop OS, use it daily
* [ ] [pwn.college](https://pwn.college/linux-luminarium/) - #linux luminarium. basic linux course
* [ ] learn [bash scripting](https://linuxhandbook.com/courses/bash/) - for loops, functions, variables, special chars, arrays. just read the articles if you have programming experience
* [ ] [overthewire bandit](https://overthewire.org/wargames/bandit/) (**optional**) level 0-20 #linux intro. classic wargame on linux, cbs, basic utilities. read writeups when stuck, but try to do everything on your own ^0accf7
* [ ] [pwn.college](https://pwn.college/fundamentals/program-misuse/) - program misuse - basic privilege escalation on linux using standard utilities #privesc_I
* [ ] [pwn.college](https://pwn.college/fundamentals/data-dealings/) - data & encoding 

# Core - C, coding, SQL, computer networks, crypto and tools

> [!about Ecole42 / school21]
> In this module School 21 / Ecole42 projects (School 21 is a Russian version of Ecole42) are suggested. You can use alternative path if you are not a school 21 / Ecole42 student. The most important thing about School 21 /  Ecole 42 is that it is a programming school, learning how to code is extremely helpful for CbS.
> Starting from 10th project in School 21, the most fundamental topics are completed and specialization is started. This projects are focused on CbS engineering rather than offensive security so I decided to make them optional though some of the concepts are relevant and helpful (especially 12th and 13 projects)

## Core CbS Ecole42 / School 21 projects ([[🧭 CyberSecurity roadmap. Starting point#^29096b|Alternative]] if you are not Ecole 42 / school 21 student):
### School 21 / Ecole42 C bootcamp #C #coding #memory_management #git #gdb
>Learn coding, memory and low-level concepts. Very good foundation for CbS specialist and preparation for the third [[🧭 CyberSecurity roadmap. Starting point#^114cf4|roadmap]] in the future
- [ ] C bootcamp 
### School 21 / Ecole42 sql bootcamp #SQL
- [ ] SQL bootcamp 
### School 21 / Ecole42 devops projects
- [ ] don't go too deep, make a couple of projects on linux, networks, automation and docker

### School 21 CbS projects
#### School 21 CbS 1-4 projects #networks_I #gns3 #wireshark
* [ ] s21_1 ✅ 
* [ ] s21_2 ✅
* [ ] s21_3 ✅ 
* [ ] s21_4 ✅ 
#### School 21 CbS 5-9 projects #linux #windows #crypto
* [ ] s21_5 ✅  linux basics
* [ ] s21_6 ✅  windows basics
* [ ] s21_7 ✅  crypto_intro
* [ ] s21_8 ✅  crypto_symetric
* [ ] s21_9 ✅  crypto_asymetric
### optional School 21 CbS projects:
* [ ] s21_10 - data channel protection #openVPN #NGate #TLS #pki
* [ ] s21_11 - Enterprise_IT_landscape
* [ ] **s21_12** - network attacks #mitmproxy and basic pentesting tools
* [ ] **s21_13** - threat detection and #yara, #suricata, #behavioral_analysis
* [ ] s21_14 - Designing secure network #NGFW #pfsense, #IPSec VPN #iptables
* [ ] s21_15 - Russian CbS legislation
* [ ] s21_16 - project lifecycle
* [ ] s21_17 - physical security
* [ ] s21_18 - social engineering and #OSINT
### Ecole42 CbS projects
* [ ] Review and complete the most important CbS projects in Ecole42, especially on topics like networks, crypto, linux. Don't go too deep - start doing CTFs and other parts of this roadmap ASAP
## Alternative track for Core:

^29096b
### Intro to computer science and technical security
* [ ] [CS50](https://youtube.com/playlist?list=PLhQjrBD2T380hlTqAU8HfvVepCcjCqTg6&si=6fRP30JMlcproLeo) (optional) - legendary Stanford introduction to computer science. Gives you basic understanding of C and coding, memory, algorithms, data structures and how computer works. You can drop AI part. This course includes not only lectures abut also [problem set](https://cs50.harvard.edu/x/) Updated every year. If pacing seems a bit slow - skip this part.
* [ ] Great fundamental [course](https://www.roppers.org/courses/technical-security-fundamentals) about technical security 

### Tools
#### #vim (optional but HIGHLY recommended) 
- [ ] learn vim and configure neovim:
	Just install vim and type in terminal `vimtutor`. Follow the instructions. Then download vim cheatsheet and try write everything in vim, checking with cheatsheet. Then configure neovim with plugins such as auto complete and themes.
> OR 
- [ ] install and learn emacs 
#### #Git:
fun git games for learning git. Try to learn git by doing, don't waste your time on "studying" git
- [ ] https://gitmastery.me/intro/
- [ ] https://learngitbranching.js.org
#### virtualization and containerization:
 - [ ] learn basic virtualization and containerization (docker [intro](https://docs.docker.com/get-started/introduction/) and [labs](https://docs.docker.com/guides/?tags=labs))
 > just read articles, watch youtube lectures, then deploy VMs in KVM/Virtualbox. Run some docker containers - learn about isolation, basic docker networking
### #C :
- [ ] Learn [basic Syntax](https://www.learn-c.org)
- [ ] github roadmap [learn C in 60 days](https://github.com/Sckab/C-RoadMap/tree/master) ^a97ce8
> OR find, review and complete other courses that cover C programming.
- [ ] build a C/C++ pet project, you can review some C/C++ project ideas [here](https://github.com/Xtremilicious/projectlearn-project-based-learning)(suggested: tetris, sudoku, chess etc)
- [ ] learn how to use valgrind and gdb
> **Use Valgrind to check for memory leaks**, push code to github/gitlab and use clang-format. This will teach you how to think like a programmer as well as some low-level concepts. This is also a preparation for the third [[🧭 CyberSecurity roadmap. Starting point#^114cf4|roadmap]] 


### #sql:
- [ ]  [pwn.college](https://pwn.college/fundamentals/sql-playground/) + this [course](https://sqlbolt.com) + and [this](https://www.w3schools.com/sql/)(for reference) **OR / AND:** RU free sql [course](https://sql-academy.org/ru)

### #crypto:
- [ ] [pwn.college](https://pwn.college/intro-to-cybersecurity/cryptography/) - crypto module on pwn.college
> OR / AND:
- [ ] [cryptohack](https://cryptohack.org/challenges/) additional course on crypto
- [ ] https://www.khanacademy.org/computing/computer-science/cryptography - additional course on crypto from khan academy, helpful and illustrative but not that deep (**optional**)

### #networks :
- [ ] https://www.roppers.org/courses/networking  - very practical course 
	> optional:
- [ ] https://www.professormesser.com/netplus-resources/
	> OR / AND: 
- [ ] [computer networks - top down approach by J. Kurose](https://gaia.cs.umass.edu/kurose_ross/online_lectures.htm) - a great introductory course with interactive labs. There is also a book by this author.
	
* Additional courses:
	* Russian-lang courses: [A. Sozykin](https://www.youtube.com/playlist?list=PLtPJ9lKvJ4oiNMvYbOzCmWy6cRzYAh9B1)
	* more advanced networking courses and network security in [[🏴Pentest roadmap#^9ad11f]]. You don't need CCNA at this point, but you need to know basics - you can try CISCO courses in that roadmap or CCNA if you are **really** interested in networks.



# Web pentest I and CTF warm-up
^dcbdf9
## HTB pentest intro:
* [ ] [Starting point](https://app.hackthebox.com/starting-point?tab=1) - free labs, pentest introduction, both #infra and #web covered, as well as #privesc_I 
*   active machines on HTB (optional for this roadmap, but very useful in general)

## WEB pentest I:
### pwn.college
 - [ ] pwn.college [talking web](https://pwn.college/fundamentals/talking-web/) - foundational knowledge about web, HTTP, cookies, json etc
 - [ ] pwn.college [web-security](https://pwn.college/intro-to-cybersecurity/web-security/)
### overthewire web wargame:
* [ ] [overthewire natas](https://overthewire.org/wargames/natas/)  (level 0-30) - legendary wargame for getting into web pentest #web 

> if you are planning to do [[🧭 CyberSecurity roadmap. Starting point#^114cf4|Vulnerability research roadmap]], you can skip THM labs:
### [THM](https://tryhackme.com) #web_I rooms (**optional**):

* [ ] install and learn burp [suite](https://tryhackme.com/room/burpsuiterepeater) 
> OR / AND:
* [ ] install and learn [OWASP ZAP](https://tryhackme.com/room/learnowaspzap) ^a0641b

>some links might be broken, search alternatives on [THM](https://tryhackme.com) and [here](https://github.com/Hunterdii/TryHackMe-Roadmap#web)
#### 🧱 1. Fundamentals of Web technologies
* [ ] [TryHackMe | HTTP in detail](https://tryhackme.com/room/httpindetail)
* [ ] [TryHackMe | How website work](https://tryhackme.com/room/howwebsiteswork)
* [ ] [TryHackMe | Walking An Application](https://tryhackme.com/room/walkinganapplication)
* [ ] [TryHackMe | Web Application Basics](https://tryhackme.com/room/webapplicationbasics)

#### 🧠 2. An introduction to vulnerabilities
* [ ] [TryHackMe | Vulnerabilities 101](https://tryhackme.com/room/vulnerabilities101)
* [ ] [TryHackMe | OWASP Top 10](https://tryhackme.com/room/owasptop10)
* [ ] [TryHackMe | OWASP Top 10 - 2021](https://tryhackme.com/room/owasptop102021)
* [ ] [TryHackMe | Web Application Security](https://tryhackme.com/room/webapplicationsecurity)

#### 🔐 3. Injections
- [ ] [TryHackMe |SQL injection](https://tryhackme.com/room/sqlinjectionlm)
- [ ] [TryHackMe |SQLmap](https://tryhackme.com/room/sqlmap)
* [ ] [TryHackMe | Advanced SQL Injection](https://tryhackme.com/room/advancedsqlinjection)
* [ ] https://tryhackme.com/room/sch3mad3mon
* [ ] [TryHackMe | NoSQL Injection](https://tryhackme.com/room/nosqlinjectiontutorial)

#### ⚙️ 4. Input validation and crawls
* [ ] [TryHackMe | XSS](https://tryhackme.com/room/axss)
* [ ] [TryHackMe | SSTI](https://tryhackme.com/room/ssti)
* [ ] [TryHackMe | File Inclusion, Path Traversal](https://tryhackme.com/room/filepathtraversal)
* [ ] [TryHackMe | SSRF](https://tryhackme.com/room/ssrf)

#### 5. 🌐 Business logic and access control
* [ ] [TryHackMe | OWASP Broken Access Control](https://tryhackme.com/room/owaspbrokenaccesscontrol)
* [ ] [TryHackMe | CSRF](https://tryhackme.com/room/csrfV2)
* [ ] [TryHackMe | IDOR](https://tryhackme.com/room/idor-aoc2025-zl6MywQid9)

#### 🧩 6. Advanced attacks on HTTP
* [ ] [TryHackMe | HTTP Request Smuggling](https://tryhackme.com/room/httprequestsmuggling )
* [ ] [TryHackMe | HTTP/2 Request Smuggling](https://tryhackme.com/room/http2requestsmuggling)
* [ ] [TryHackMe | Microservices Architectures](https://tryhackme.com/room/microservicearchitectures)

#### 🛠️ 7. Practice on the stands (Polygons)
* [ ] [TryHackMe / DVWA](https://tryhackme.com/room/dvwa )
* [ ] [TryHackMe | WebGOAT](https://tryhackme.com/room/webgoat)
* [ ] [TryHackMe | OWASP Mutillidae II](https://tryhackme.com/room/mutillidae)
* [ ] [TryHackMe | OWASP Juice Shop](https://tryhackme.com/room/owaspjuiceshop)

#### 8. 🚩 Real CTF-like rooms 

> [!CTF tasks for warming up before CTF (optional)] 
> * https://github.com/Hunterdii/TryHackMe-Roadmap?tab=readme-ov-file#easy-ctf - #ctf  tasks and other free labs
> * [ ] https://www.youtube.com/playlist?list=PLqGS6O1-DZLpKpmKnwp9LB_92WAQdHbks - #web rooms

* [ ] [TryHackMe | Vulnversity](https://tryhackme.com/room/vulnversity)
* [ ] [TryHackMe | Overpass](https://tryhackme.com/room/overpass)
* [ ] [TryHackMe | Ignite](https://tryhackme.com/room/ignite)
* [ ] [TryHackMe | Jack-of-All-Trades](https://tryhackme.com/room/jackofalltrades)
* [ ] [TryHackMe | Bolt](https://tryhackme.com/room/bolt)
* [ ] [TryHackMe | Year of the Rabbit](https://tryhackme.com/room/yearoftherabbit)
* [ ] [TryHackMe | Develpy](https://tryhackme.com/room/develpy)
* [ ] [TryHackMe | VulnNet](https://tryhackme.com/room/vulnnet)
* [ ] [TryHackMe | Juicy Details](https://tryhackme.com/room/juicydetails )
* [ ] [TryHackMe | TakeOver](https://tryhackme.com/room/takeover )
* [ ] [TryHackMe | Corridor](https://tryhackme.com/room/corridor )
* [ ] [RootMe](https://tryhackme.com/room/rrootme ) — *Classic for beginners.*
* [ ] [Pickle Rick](https://tryhackme.com/room/picklerick )
* [ ] [Simple CTF](https://tryhackme.com/room/easyctf)
* [ ] [Merry XSS-Mas](https://tryhackme.com/room/xss-aoc2025-c5j8b1m4t6) - CTF-style XSS room


> BlueTeam is optional for [[🧭 CyberSecurity roadmap. Starting point#^114cf4|Vulnerability research roadmap]]
# BlueTeam courses - forensics intro (**optional**)

## forensics intro:
* [ ] [HackTheBox Sherlocks](https://app.hackthebox.com/sherlocks) and [challenges](https://app.hackthebox.com/challenges) - basic #forensics. Don't go too deep. This is included in this roadmap because forensics tasks are often included as test task for interns and also a part of CTF.
## (**optional**) Entry-level blue team/SOC courses for landing first job in cybersec:
* [ ] Try Hack Me SOC L1
* [ ] [LetsDefend SOC path](https://app.letsdefend.io/path/soc-analyst-learning-path)
* [ ] free [TryHackMe](https://github.com/AtikBagwan00/tryhackme-soc-free-labs) BlueTeam rooms. Some of them are  VIP/paid, especially connected to SIEM, others are free
# Next => specialization
> At this point you have completed first CbS roadmap, congratulations. You can learn more advanced topics in the following roadmaps
* [ ] start here: [[🏴Pentest roadmap]] OR [[🧭 CyberSecurity roadmap. Starting point#^114cf4|Vulnerability research roadmap]]

---
# labs, CTF challenges, courses

^8af021

| Category                         | Resources                                                                                                                                                                                                                                                                            |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 🌐 **Web**                       | 🟣 **[PortSwigger]()**  **[[🏴Pentest roadmap#^cf620a\|local web apps]]**                                                                                                                                                                                                            |
| 💣 **Binary** / 🧠 **Reverse**   | 🔵 **[pwn.college](https://pwn.college/dojos)** / [Nightmare](https://guyinatuxedo.github.io/) / [picoCTF](https://picoctf.org/get_started.html) [ROP challenges](https://ropemporium.com/) [crackmes](https://crackmes.one) [pwnable.kr](https://pwnable.kr)                        |
| 🔍 **Forensics**                 | 🟢 **[HTB sherlocks](https://app.hackthebox.com/sherlocks)** => [letsDefend DFIR path](https://app.letsdefend.io/path/dfir-learning-path) / [THM](https://tryhackme.com) / [picoCTF](https://picoctf.org/get_started.html)                                                           |
| 🔍 **OSINT / Stegano**           | 🟢 [HTB challenges](https://app.hackthebox.com/challenges) / [THM](https://tryhackme.com) / [picoCTF](https://picoctf.org/get_started.html)                                                                                                                                          |
| 🐧 **Linux / privesc**           | **[overthewire](https://overthewire.org/wargames/bandit)** =>**[THM](https://tryhackme.com)** => 🟡 **[pwn.college privesc](https://pwn.college/privilege-escalation~6d04fe7a/)** => **[VulnHub](https://vulnhub.com)** / **[HTB](https://app.hackthebox.com/starting-point?tab=1)** |
| 🏢 **AD**                        | 🟢 [[🏴Pentest roadmap#^f30dd9\|GOAD Game of Active Directory]]                                                                                                                                                                                                                      |
| ☁️ **Cloud**                     | ☁️ [[☁️cloud CbS roadmap#^a0b546\|yandex cloud courses]] / [[☁️cloud CbS roadmap#^885d58\|CloudGOAT (AWS)]]                                                                                                                                                                          |
| 🧱 **Sandbox escape**            | 🔵 **[pwn.college](https://pwn.college/dojos)** / [Vulnhub](https:\/\/vulnhub.com)                                                                                                                                                                                                   |
| 🔒 **Crypto**                    | [cryptohack](https://cryptohack.org/challenges/) / [pwn.college - crypto](https://pwn.college/intro-to-cybersecurity/cryptography/)                                                                                                                                                  |
| 🏴 **CTF / universal platforms** | [picoCTF](https://picoctf.org/get_started.html) / [Hacker101 CTF](https://ctf.hacker101.com/) / [THM](https://tryhackme.com) / [HTB](https://app.hackthebox.com/starting-point?tab=1)                                                                                                |
 ^d87ae9
more [links](https://github.com/Crypto-Cat/CTF)

---
## 📚 Books, lectures, courses

* Computer Networks
	- CCNA FULL COURSE with labs (very big) - [jeremy's IT lab](https://www.youtube.com/playlist?list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ)
	- J. Kurose[ Computer Networks - top down approach](https://youtube.com/playlist?list=PL1ya5dD_M8uX-BLUF1FEvUNsYWQL5_l0O&si=t8fRaDZigZCYh5y5) (video)
	- Computer Networks, A. Tanenbaum
- Pentest:
	- **[Stanford web security course](https://www.youtube.com/playlist?list=PL1y1iaEtjSYiiSGVlL1cHsXN_kvJOOhu-)**, [text version](https://web.stanford.edu/class/cs253/) ^5162dc
	- Yandex security [course](https://youtube.com/playlist?list=PLQC2_0cDcSKD_JHWtEJGIFQUVh7Z5JM8E&si=L_K0djnH6f5jEeD_) (RU) ^45da8d
	* [**Practical Ethical Hacking (Free 12h Course)**](https://www.youtube.com/watch?v=3Kq1MIfTWCE) - TCM Security's high-quality introductory course on YouTube.
	- "The Web Application Hacker's Handbook: Finding and Exploiting Security Flaws" by D. Stuttard and M. Pinto is an indispensable book from the creators of Burp Suite.
	- "Web penetration Testing with Kali Linux" by G. Najera-Gutierrez and J. A. Ansari is worth reading, memorizing and using as a reference.
	- "The Hacker Playbook: Practical Guide To Penetration Testing" by P. Kim - each edition describes the popular tools used by red team at the release date.
	- "Protocol-level network attack" by D. Forshaw - this work is also worth reading.
	* [**Metasploit Unleashed**](https://www.offsec.com/metasploit-unleashed/) - The most complete free guide to Metasploit by OffSec.
* Linux/Unix/OS:
	* UNIX and Linux System Administration Handbook by Evi Nemeth 
	* Modern Operating Systems, A. Tanenbaum
* Reverse/pwn:
	- [assembler is easy](https://books.google.ru/books?id=djgHlWWCnMwC&printsec=frontcover&hl=ru&source=gbs_atb#v=onepage&q&f=false) - Oleg Kalashnikov (RU)
	- jon erickson hacking art of exploitation
	-  Фундаментальные основы хакерства, Крис Касперски (RU)
	- отладка программ без исходного кода, Крис Касперски (RU)
	* Reverse engineering for beginners, D. Yurichev
	* Binary exploitation [playlist](https://www.youtube.com/playlist?list=PLhixgUqwRTjxglIswKp9mpkfPNfHkzyeN)
	* WannaCry malware [analysis](https://www.youtube.com/playlist?list=PLniOzp3l9V83Yf52IXJTvW9rjstdqkduP) 


[^1]: these languages were chosen because: C/C++ are very fundamental in terms of CS in general, knowing C helps in reverse engineering and binary exploitation, C++ is used for creating malware and most desktop apps, as well as apps for critical infrastructure and embedded. Rust is memory-safe and will replace C/C++ in most critical infrastructure, Go is efficient for backend and has some interesting concepts. Java is best choice for appsec and reverse engineer / vulnerability researcher. General advice: if you want to do pentest - choose go, otherwise choose Java. Python is not included because it is a default scripting language for pentest, you should know it at this point. JS is not included because you should learn it by doing WEB pentesting at basic level - going too deep in frontend is pointless. PHP is not included because it is becoming almost legacy.

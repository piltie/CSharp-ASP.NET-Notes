<h4>My REST API note-taking, w/ some concepts and tools I'm currently using on my project.</h4>
![[genshin-impact-genshin.gif|center]]
<span style="color: grey;"><i>(Made using obsidian, Pink Theme)</i></span>

<h1><span style="font-size: 0.8em;">💕</span> Dependency Injection and DTOS</h1>

<span style="background-color:#e8b2a4; color: white;">♦️ Dependency Concept:</span>

![[Pasted image 20221101100758.png]]

<span style="background-color:#e8b2a4; color: white;">♦️ Dependency Inversion Principle:</span>

![[Pasted image 20221101100845.png]]

♦️ Code is cleaner, easier to modify and reause, and by using abstracions (interface) we are decoupling implementations from each other.
<span style="background-color:#e8b2a4; color: white;">♦️ Data Transfer Object (DTO):</span> Actual contract that’s going to be enabled between the client and our service.

<h1><span style="font-size: 0.8em;">💕</span> Entities</h1>
♦️ Entities folder - Used record type instead of the traditional class (it's for immutable objects; allows init-only properties target-typed expressions, which I used in the controller).
♦️ Persistence - Files (in-memory repository) or Database (relation or no-sql).
♦️ Repository - I added a in-memory repository (that resets when the project is rebooted), then I replaced it w/ a no-sql database (MongoDB, running it as a docker container), viewed using a VSCode extension.

💟 POST, GET, PUT, DELETE - I only used those methods (and set a specified response for each, in case of sucess or error). Swagger let me test those right away, but Postman is more complete.

<h1><span style="font-size: 0.8em;">💕</span> Dockers</h1>
♦️ Docker Image: A standalone package of software that includes everything needed to run an application.
♦️ Docker Container: A runtime instance of a Docker image.
♦️ Docker Engine: The container runtime.

💟 OBS: Had to download docker desktop v2 so it runs in my deprecated windows ver.

![[red_queen.gif]]
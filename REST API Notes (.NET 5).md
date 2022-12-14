<h4>My REST API note-taking, w/ some concepts and tools I'm currently using on my project.</h4>
![[genshin-impact-genshin.gif|center]]
<span style="color: grey;"><i>(Made using obsidian, Pink Theme)</i></span>

<h1><span style="font-size: 0.8em;">ð</span> Dependency Injection and DTOS</h1>

<span style="background-color:#e8b2a4; color: white;">â¦ï¸ Dependency Concept:</span>

![[Pasted image 20221101100758.png]]

<span style="background-color:#e8b2a4; color: white;">â¦ï¸ Dependency Inversion Principle:</span>

![[Pasted image 20221101100845.png]]

â¦ï¸ Code is cleaner, easier to modify and reause, and by using abstracions (interface) we are decoupling implementations from each other.
<span style="background-color:#e8b2a4; color: white;">â¦ï¸ Data Transfer Object (DTO):</span> Actual contract thatâs going to be enabled between the client and our service.

<h1><span style="font-size: 0.8em;">ð</span> Entities</h1>
â¦ï¸ Entities folder - Used record type instead of the traditional class (it's for immutable objects; allows init-only properties target-typed expressions, which I used in the controller).
â¦ï¸ Persistence - Files (in-memory repository) or Database (relation or no-sql).
â¦ï¸ Repository - I added a in-memory repository (that resets when the project is rebooted), then I replaced it w/ a no-sql database (MongoDB, running it as a docker container), viewed using a VSCode extension. Don't forget to add the MongoDB settings file + adding it in the appsetting.json.

ð POST, GET, PUT, DELETE - I only used those methods (and set a specified response for each, in case of sucess or error). Swagger let me test those right away, but Postman is more complete.

<h1><span style="font-size: 0.8em;">ð</span> Dockers</h1>
â¦ï¸ Docker Image: A standalone package of software that includes everything needed to run an application.
â¦ï¸ Docker Container: A runtime instance of a Docker image.
â¦ï¸ Docker Engine: The container runtime.

ð OBS: Had to download docker desktop v2 so it runs in my deprecated windows ver.

![[red_queen.gif]]

<h1><span style="font-size: 0.8em;">ð</span> Synchronous & Asynchronous Programming</h1>
â¦ï¸ Async all the way: 

![[Pasted image 20221101113004.png]]

â¦ï¸ From Sync to Async (At the interface and repository):
	1. Add "Async" at the end of the method's name (naming convention, F2 hotkey);
	2. Methods needs to return Task<T> instead of <T>;
	4. Instead of getting the <T> result right away from the method, as in synchronous methods, instead you're getting a task that represents an asynchronous operation that eventually is going to return the <T> result, whenever it has finished retrieving it from the database;
	5. In void cases, just turn into Task;
	6. Add async and await (syntactic sugar) at the repository functions.


<h1><span style="font-size: 0.8em;">ð</span> Handling secrets</h1>
â¦ï¸ .NET Secrets manager for storing passwords and other sensitive info, instead of adding it in the appsettings.json.

<h1><span style="font-size: 0.8em;">ð</span> Health checks</h1>
â¦ï¸ Health checks:

![[Pasted image 20221101155618.png]]

â¦ï¸ Add it in configuration services and middleware. Call it using GET (https://localhost:44366/health).
â¦ï¸ For MongoDb: Add the NuGet package and configure it in startup.cs.
â¦ï¸ The pattern is to specify both a ready endpoint (/health/ready -> is the service ready to receive requests?) and a live endpoint (/health/live -> is the service alive?).
â¦ï¸ Predicate: The way that you can filter out which health checks you want to include in that endpoint;
â¦ï¸ List of other health checks: https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks



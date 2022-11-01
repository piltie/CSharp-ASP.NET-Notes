<h4>Important commands cheatlist and related notes.</h4>
<h1><span style="font-size: 0.8em;">💕</span> Cygwin</h1>
$ cd with \\\\ instead of \
$ grep -w 'STRING' *
$ grep -r 'STRING' //directory1/directory2

<h1><span style="font-size: 0.8em;">💕</span> Dockers + MongoDB</h1>
docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db mongo
docker ps (check if everything is ok)
docker stop mongo
docker volume ls
docker volume rm mongodbdata
docker volume prune (delete all volumes)

docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=Pass#word1 mongo

<h1><span style="font-size: 0.8em;">💕</span> Git</h1>
git init (if it's the first time) -> git add . -> git status -> git commit -> git push -u origin main

git remote -v 

git remote add origin https://github.com/piltie/piltie.github.io.git

git config --global http.proxy http[s]://usuario:senha@proxy:porta

git config --global user.email 95034183+piltie@users.noreply.github.com

https://stackoverflow.com/questions/42830557/git-remote-add-origin-vs-remote-set-url-origin

💟 IF SOMETHING GOES WRONG TRY THESE:
git config --global --unset http.proxy
git -c http.sslVerify=false clone 
git -f pra forçar

<h1><span style="font-size: 0.8em;">💕</span> .NET Secret Manager</h1>
dotnet user-secrets init (creates a new id at the .csproj file)
dotnet user-secrets set name:property value (dotnet user-secrets set MongoDbSettings:Password Pass#word1)

<h1><span style="font-size: 0.8em;">💕</span> MongoDb Health Checks</h1>
dotnet add package AspNetCore.HealthChecks.MongoDb (NuGet package)
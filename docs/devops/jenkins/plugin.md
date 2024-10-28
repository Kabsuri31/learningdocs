            PLUGIN
Role based access strategy      
Docker pipeline     
Git             



            Auto trigger build from github

- Configure git check out to your build job
- go to job and enable "Github hook trigger for GITScm polling"     
   <i style="color:blue">When Jenkins receives a GitHub push hook, GitHub Plugin checks to see whether the hook came from a GitHub repository which matches the Git repository defined in SCM/Git section of this job. If they match and this option is enabled, GitHub Plugin triggers a one-time polling on GITScm. When GITScm polls GitHub, it finds that there is a change and initiates a build. The last sentence describes the behavior of Git plugin, thus the polling and initiating the build is not a part of GitHub plugin.</i>
- Go to github repository settings and to webhook and configure webhook (https://jenkins_url/github-webhook/)
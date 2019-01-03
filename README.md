# MediaWiki Deployment

All information below is a reference from [MediaWiki](https://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Red_Hat_Linux) page

### Required software to install mediawiki on a Docker container
1. centos7+ docker image
2. systemd, httpd, wget, vim
3. php71-php, php71-php-mbstring, php71-php-mysqlnd, php71-php-gd, php71-php-xml, mariadb-server, mariadb


**What's in aws-terraform-cluster? and what's done?**
- Terraform file `terraform-aws-update.yml` that will provision 2 EC2 instances with a load balancer on AWS
- Installed Apache on both EC2 instances
- Copied basic template of index.html on both ec2 instances to see if the web page is loading(used different colors on both index.html) and balancing the traffic on either ec2 instance using load balancer.
- Finally, used the amazon ELB(elastic load balancer) dns name to browse the web app on browser.

**What's in docker-compose-mediawiki? and what's done?**
- Docker compose file `docker-compose.yml` that will create 2 docker containers, one running with mediawiki and another with mysql.
- Exposed container port running mediawiki onto localhost port and was able to browse the application on chrome. 

**What's in kubernetes-cluster? and what's done?**
- Initially I thought of running the mediawiki app on two pods and use a service to expose the webapp. But used master and minions concept. This was a little challenging task and I needed some more time to achieve it.
- This is still in progress and uploaded it as I couldn't spend more time at that point. 

**What's in wiki-deployment-docker? and what's done?**
- This was my initial try, I did not use mediawiki docker image directly but was little curios and tried to install PHP, Apache on a centOS docker image and tried to run the mediawiki web app, infact I installed few plugins manually after creating docker container. So far, I acheived what I was hoping in this task.
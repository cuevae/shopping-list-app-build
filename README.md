# shopping-list-app-build
Building elements for Shopping List App

Requirements:

- Git
- Vagrant
- VirtualBox
- Ansible

Steps:

0. Create a folder where you want to set up the builder and the app
1. git clone https://github.com/cuevae/shopping-list-app-build.git
2. cd shopping-list-app-build
3. vagrant up
4. vagrant ssh sla-host
5. cd /vagrant/shopping-list-app

*To view the app using your mobile:
6. yarn start --no-dev (I use --no-dev flag so devtools is not currently working in sla-host)
7. Use expo client app to scan the QR produced and see the application in your mobile

*Otherwise, to view the app using a web browser:
6. yarn start --web-only
7. Open your browser in the host machine and navigate to https://localhost:8086 to see the app

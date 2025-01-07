set date in docker :

	# set date first in main os ubuntu
	# sudo timedatectl set-timezone Asia/Jakarta

	# set on docker-compose.yml
	version: '3'
	services:
	  oauth:
		build: .
		volumes:
		  - .:/usr/src/app
		  - /usr/src/app/node_modules  # To prevent overwriting node_modules if installed in the container
		  - /etc/localtime:/etc/localtime:ro
		  - /etc/timezone:/etc/timezone:ro
		ports:
		  - "3007:3007"
		restart: always
		environment:
		  - NODE_ENV=development

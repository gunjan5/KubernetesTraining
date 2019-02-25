build_mac: 
		go build -o code/bin/darwin/excuse code/

build_linux: 
		GOOS=linux GOARCH=amd64 go build -o code/bin/linux/excuse code/

image: 
		docker build -t gunjan5/excuse:v1.0 .

dryrun: 
		docker run -p 8080:8080/tcp gunjan5/excuse:v1.0

pushimage:
		docker push gunjan5/excuse:v1.0

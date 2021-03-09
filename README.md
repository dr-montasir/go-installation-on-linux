## Customized installation Golang on Linux



### COMPILERS FOLDER

Example: `mkdir {compilers,compilers/c,compilers/go,compilers/rust}`

```bash
mkdir {compilers,compilers/go}
cd compilers/go
```



### VERSION 

```bash
mkdir go1.16.linux-amd64 && cd go1.16.linux-amd64
```



### DOWNLOAD

```bash
wget https://dl.google.com/go/go1.16.linux-amd64.tar.gz
```

* Write the command `dir` then hit `Enter` to check if the folder `go1.16.linux-amd64.tar.gz` is completely downloaded.



### EXTRACT & REMOVE

```bash
tar -xvf go1.16.linux-amd64.tar.gz
```

```bash
rm go1.16.linux-amd64.tar.gz
```



### WORK SPACE

```bash
cd ~
mkdir dev/golang/workspace
cd dev/golang/workspace
mkdir {bin,pkg,src,src/github.com,src/github.com/your-github-name}
```



### PATH

Open the terminal path file by writing

```bash
gedit $HOME/.bashrc
```

OR

```bash
gedit ~/.bashrc
```

`Copy`, `Paste` & `Save` the following code at the end of the `.bashrc` file, then close it.

```bash
## Changes made to the .bashrc file by myself
## GOROOT
export GOROOT=$HOME/compilers/go/go1.16.linux-amd64/go
export PATH=$PATH:$GOROOT/bin

## GOPATH
export GOPATH=$HOME/dev/golang/workspace
export PATH=$PATH:$GOPATH/bin

## GOBIN
export GOBIN=${GOPATH}/bin
```



### CHECK

Close the terminal and open it again

```go
go version
```

* `go version go1.16 linux/amd64`

```go
go env
```

* `GOPATH="/home/<your-usr-name>/dev/golang/workspace"`
* `GOBIN="/home/<your-usr-name>/dev/golang/workspace/bin"`
* `GOROOT="/home/<your-usr-name>/compilers/go/go1.16.linux-amd64/go"`
* `GOCACHE="/home/<your-usr-name>/.cache/go-build"`
* `GOENV="/home/<your-usr-name>/.config/go/env"`
* **`GOMODCACHE="/home/<your-usr-name>/dev/golang/workspace/pkg/mod"`**
* **`GOTOOLDIR="/home/montasir/compilers/go/go1.16.linux-amd64/go/pkg/tool/linux_amd64"`**



### TEST PROJECT

```bash
go get github.com/gorilla/mux
cd dev/golang/workspace/src/github.com/your-github-name
git clone https://github.com/dr-montasir/go-rest-api.git
```

```bash
cd go-rest-api/go-mock-rest-api
```

```GO
go build
```

The terminal will return the following message:

````bash
go: cannot find main module, but found .git/config in /home/usr-name/dev/golang/workspace/src/github.com/your-github-name/go-rest-api
	to create a module there, run:
	cd .. && go mod init
```

```GO
go mod init
```

The terminal again will return the next message:

```bash
go: creating new go.mod: module github.com/your-github-name/go-rest-api/go-mock-rest-api
go: to add module requirements and sums:
	go mod tidy
```

```GO
go mod tidy
```

The terminal will inform about the presence of the package `gorilla/mux`

```bash
go: finding module for package github.com/gorilla/mux
go: found github.com/gorilla/mux in github.com/gorilla/mux v1.8.0
```

```GO
go build
```

```go
go run main.go
```

OR

```GO
./go-mock-rest-api
```

Open your browser and test the project

```cmd
http://localhost:1400/api/courses
```

```json
[{"id":"1","category":"Web Development","title":"Build Web Apps with Go Language","instructor":{"firstName":"Rob","lastName":"Pike"},"cousreDuration":"4 months"},{"id":"2","category":"Mobile App Development","title":"Build Mobile Apps with Flutter Dart","instructor":{"firstName":"Lars","lastName":"Bak"},"cousreDuration":"5 months"}]
```



### OLD VERSIONS

* **[go1.15.7 linux/amd64](https://github.com/dr-montasir/go-installation-on-linux/blob/master/versions/go1.15.7.linux-amd64.md)**


## Customized installation Golang on Linux



### COMPILERS FOLDER

Example: `mkdir {compilers,compilers/c,compilers/go,compilers/rust}`

```bash
mkdir {compilers,compilers/go}
cd compilers/go
```



### VERSION 

```bash
mkdir go1.16.2.linux-amd64 && cd go1.16.2.linux-amd64
```



### DOWNLOAD

```bash
wget https://dl.google.com/go/go1.16.2.linux-amd64.tar.gz
```

* Write the command `dir` then hit `Enter` to check if the folder `go1.16.2.linux-amd64.tar.gz` is completely downloaded.



### EXTRACT & REMOVE

```bash
tar -xvf go1.16.2.linux-amd64.tar.gz
```

```bash
rm go1.16.2.linux-amd64.tar.gz
```



### WORK SPACE

`IF there is no such file or directory "~/dev/golang/workspace", then create this directory`

```bash
mkdir {dev,dev/golang,dev/golang/workspace}
```

`Or go to the Golang development directory like so`

```bash
cd ~/dev/golang/workspace
```
**`Workspace required to enable Golang versions`**

```bash
mkdir go1.16.2 && cd go1.16.2
mkdir {bin,pkg,src,src/github.com,src/github.com/your-github-name}
```
`An example of what a workspace looks like`

```bash
workspace
├── go1.15.7
├── go1.16
└── go1.16.2
    ├── bin
    ├── pkg
    └── src
        └── github.com
            └── your-github-name
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
export GOROOT=$HOME/compilers/go/go1.16.2.linux-amd64/go
export PATH=$PATH:$GOROOT/bin

## GOPATH
export GOPATH=$HOME/dev/golang/workspace/go1.16.2
export PATH=$PATH:$GOPATH/bin

## GOBIN
export GOBIN=${GOPATH}/bin
```



### CHECK

Close the terminal and open it again

```go
go version
```

* `go version go1.16.2 linux/amd64`

```go
go env
```

* `GOPATH="/home/<your-usr-name>/dev/golang/workspace/go1.16.2"`
* `GOBIN="/home/<your-usr-name>/dev/golang/workspace/go1.16.2/bin"`
* `GOROOT="/home/<your-usr-name>/compilers/go/go1.16.2.linux-amd64/go"`
* `GOCACHE="/home/<your-usr-name>/.cache/go-build"`
* `GOENV="/home/<your-usr-name>/.config/go/env"`
* **`GOMODCACHE="/home/<your-usr-name>/dev/golang/workspace/go1.16.2/pkg/mod"`**
* **`GOTOOLDIR="/home/montasir/compilers/go/go1.16.2.linux-amd64/go/pkg/tool/linux_amd64"`**



### TEST PROJECT

```bash
go get github.com/gorilla/mux
cd dev/golang/workspace/go1.16.2/src/github.com/your-github-name
git clone https://github.com/dr-montasir/go-rest-api.git
```

```bash
cd go-rest-api/go-mock-rest-api
```

```GO
go build
```

The terminal will return the following message:

```bash
go: cannot find main module, but found .git/config in /home/usr-name/dev/golang/workspace/go1.16.2/src/github.com/your-github-name/go-rest-api
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



#### How to test the project outside of GOPATH?

```bash
cd ~/Desktop
git clone https://github.com/dr-montasir/go-rest-api.git
cd go-rest-api/go-mock-rest-api
go build
```

`go: cannot find main module, but found .git/config in /home/usr-name/Desktop/go-rest-api
	to create a module there, run:
	cd .. && go mod init`

```GO
go mod init
```

`go: cannot determine module path for source directory /home/usr-name/Desktop/go-rest-api/go-mock-rest-api (outside GOPATH, module path must be specified)`

`Example usage:
	'go mod init example.com/m' to initialize a v0 or v1 module
	'go mod init example.com/m/v2' to initialize a v2 module`

```GO
go mod init go-mock-rest-api
```

`go: creating new go.mod: module go-mock-rest-api
go: to add module requirements and sums:
	go mod tidy`

```GO
go mod tidy
```

`go: finding module for package github.com/gorilla/mux
go: found github.com/gorilla/mux in github.com/gorilla/mux v1.8.0`

```GO
go build
```

OR

```GO
go build -o alternative-project-name main.go
```




### OLD VERSIONS

* **[go1.16 linux/amd64](https://github.com/dr-montasir/go-installation-on-linux/blob/master/versions/go1.16.linux-amd64.md)**
* **[go1.15.7 linux/amd64](https://github.com/dr-montasir/go-installation-on-linux/blob/master/versions/go1.15.7.linux-amd64.md)**


## Customized installation Golang on Linux



### COMPILERS FOLDER

Example: `mkdir {compilers,compilers/c,compilers/go,compilers/rust}`

```bash
mkdir {compilers,compilers/go}
cd compilers/go
```



### VERSION 

```bash
mkdir go1.15.7.linux-amd64
cd go1.15.7.linux-amd64
```



### DOWNLOAD

```bash
wget https://dl.google.com/go/go1.15.7.linux-amd64.tar.gz
```

* Write the command `dir` then hit `Enter` to check if the folder `go1.15.7.linux-amd64.tar.gz` is completely downloaded.



### EXTRACT & REMOVE

```bash
tar -xvf go1.15.7.linux-amd64.tar.gz
```

```bash
rm go1.15.7.linux-amd64.tar.gz
```



### WORK SPACE

```bash
cd ~
mkdir dev/golang/workspace
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
export GOROOT=$HOME/compilers/go/go1.15.7.linux-amd64/go
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

* `go version go1.15.7 linux/amd64`

```go
go env
```

* `GOPATH="/home/<your-usr-name>/dev/golang/workspace"`
* `GOBIN="/home/<your-usr-name>/dev/golang/workspace/bin"`
* `GOROOT="/home/<your-usr-name>/compilers/go/go1.15.7.linux-amd64/go"`



### TEST PROJECT

```bash
go get github.com/gorilla/mux
go get github.com/dr-montasir/go-rest-api
```

```bash
cd dev/golang/workspace/src/github.com/dr-montasir/go-rest-api/go-mock-rest-api
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


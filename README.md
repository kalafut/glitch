glitch
======

Continuously and automatically, build, test, and vet your go package.

Installation
------------

```shell
go get -u github.com/levicook/glitch
go install github.com/levicook/glitch
```

Usage
-----

Make sure $GOPATH/bin is on your PATH, then simply:

```shell
cd <your go package>
glitch
```

Behavior
--------

glitch will `go build ./...`, `go vet ./...` and `go test ./...` your go package.
If any one of these steps fail, it stops on that step, and waits for you to fix the issue.

When things go well, your output should look like this: 

```shell
2013/09/15 20:38:07 glitch: building
2013/09/15 20:38:07 glitch: build OK - vetting
2013/09/15 20:38:07 glitch: vet OK - testing
?       github.com/levicook/glitch      [no test files]
2013/09/15 20:38:08 glitch: test OK - wating for next build event
```

When something fails, like `go build`, you'll see less output. eg:

```shell
2013/09/15 20:42:57 glitch: building
# github.com/levicook/glitch
./main.go:83: syntax error: unexpected semicolon or newline, expecting )
```

There's nothing generic about this tool. It encapsulates a specific workflow and only
pays attention to .go files. If you want something different, use something totally
generic like guard. You're welcome to fork this, but I am unlikely to merge pull requests
looking for a different and/or pluggable behavior.


Known Issues
------------
Not a glitch issue per se; OSX users frequently see: too many open files
http://superuser.com/questions/433746/is-there-a-fix-for-the-too-many-open-files-in-system-error-on-os-x-10-7-1

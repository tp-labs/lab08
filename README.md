## Laboratory work VIII

Данная лабораторная работа посвещена изучению систем автоматизации развёртывания и управления приложениями на примере **Docker**

```ShellSession
$ open https://docs.docker.com/get-started/
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab08** на сервисе **GitHub**
- [ ] 2. Ознакомиться со ссылками учебного материала
- [ ] 3. Выполнить инструкцию учебного материала
- [ ] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
$ export GITHUB_USERNAME=<имя_пользователя>
```

```ShellSession
$ git clone https://github.com/${GITHUB_USERNAME}/lab07 lab08
$ cd lab08
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab08
```

```ShellSession
$ cat > Dockerfile <<EOF
FROM ubuntu:18.04
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

RUN apt update
RUN apt install -yy gcc g++ cmake 
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

COPY . print/
WORKDIR print
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
RUN cmake --build _build
RUN cmake --build _build --target install
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

ENV LOG_PATH /home/logs/log.txt
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

VOLUME /home/logs
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

WORKDIR _install/bin
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

CMD ./demo
EOF
```

```ShellSession
$ docker build -t logger .
```

```ShellSession
$ docker images
```

```ShellSession
$ mkdir logs
$ docker run -it -v "$(pwd)/logs/:/home/logs/" logger
text1
text2
text3
<C-D>
```

```ShellSession
$ docker inspect logger
```

```ShellSession
$ cat logs/log.txt
```

```ShellSession
$ vim README.md
:s/lab12/lab13/g<CR>
:wq
```

```ShellSession
$ vim .travis.yml
/lang<CR>o
services:
  - docker<ESC>
jVGddo
script:
  - docker build -t logger .<ESC>
```

```ShellSession
$ git add Dockerfile
$ git add .travis.yml
$ git commit -m"adding Dockerfile"
$ git push origin master
```

```ShellSession
$ travis login --auto
$ travis enable
```

## Report

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=08
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Links

- [Book](https://www.dockerbook.com)
- [Instructions](https://docs.docker.com/engine/reference/builder/)

```
Copyright (c) 2015-2019 The ISC Authors
```

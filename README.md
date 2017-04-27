## Laboratory work XIII

Данная лабораторная работа посвещена изучению систем для автоматизации развёртывания и управления приложениями на примере **Docker**

```bash
$ open https://docs.docker.com/get-started/
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab13** на сервисе **GitHub**
- [ ] 2. Выполнить инструкцию учебного материала
- [ ] 3. Ознакомиться со ссылками учебного материала

## Tutorial

```bash
$ export GITHUB_USERNAME=<имя_пользователя>
```

```bash
$ git clone https://github.com/${GITHUB_USERNAME}/lab11 lab13
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab13
$ cd lab13
```

```bash
$ cat > Dockerfile <<EOF
...
EOF
```

## Links

- [Instructions](https://docs.docker.com/engine/reference/builder/)
- [Book](https://www.dockerbook.com)

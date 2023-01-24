# Домашнее задание к занятию «8.2. Что такое DevOps. СI/СD» - Сотников Андрей

### Задание 1  

> В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

Настройки проекта:

Результаты сборки:

---

### Задание 2

> В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

```
pipeline {
    agent any
    
    tools {
        go "go:latest"
    }
    
    stages {
        stage('Git') {
            steps {
                git 'https://github.com/netology-code/sdvps-materials'
            }
        }
        stage('Test') {
            steps {
                sh 'go test .'
            }
        }
        stage('Docker_build') {
            steps {
                sh 'docker build .'
            }
        }
    }
}

```

---

### Задание 3

> В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

```pipeline {
    agent any
    
    tools {
        go "go:latest"
    }
    
    stages {
        stage('Git') {
            steps {
                git 'https://github.com/netology-code/sdvps-materials'
            }
        }
        stage('Test') {
            steps {
                sh 'go test .'
            }
        }
        stage('Go_build') {
            steps {
                sh 'go build -a -installsuffix nocgo -o /app/gofile .'
            }
        }
        stage('Push') {
            steps {
                sh "curl -v --user 'admin:ED8U8DrKnwYX8@9' --upload-file /app/gofile http://localhost:8081/repository/netology_hw/gofile"
            }
        }
    }
}
```

---

### Задание 4*

> В качестве ответа на задание прикрепите ссылку на граф коммитов <https://github.com/ваш-логин/ваш-репозиторий/network> в ваш md-файл с решением.

<https://github.com/a-sotnikov/hw_repo/network>
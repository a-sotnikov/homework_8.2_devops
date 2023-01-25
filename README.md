# Домашнее задание к занятию «8.2. Что такое DevOps. СI/СD» - Сотников Андрей

### Задание 1  

> В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

Настройки проекта:

![settings](https://github.com/a-sotnikov/homework_8.2_devops/blob/main/task1_config.png)
  
Результаты сборки:

![results](https://github.com/a-sotnikov/homework_8.2_devops/blob/main/task1_result.png)
---

### Задание 2

> В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

Настройки:
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
Результаты:

![results](https://github.com/a-sotnikov/homework_8.2_devops/blob/main/task2_result.png)
---

### Задание 3

> В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

Настройка:

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
Результаты:

![Results](https://github.com/a-sotnikov/homework_8.2_devops/blob/main/task3_result.png)

![Nexus](https://github.com/a-sotnikov/homework_8.2_devops/blob/main/task3_nexus.png)

---

### Задание 4*

> В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

Настройка:

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
        stage('Go_build') {
            steps {
                sh 'go build -a -installsuffix nocgo -o /app/gofile_v$BUILD_NUMBER .'
            }
        }
        stage('Push') {
            steps {
                sh "curl -v --user 'admin:ED8U8DrKnwYX8@9' --upload-file /app/gofile http://localhost:8081/repository/netology_hw/gofile_v$BUILD_NUMBER"
            }
        }
    }
}

```
Результаты:

![Results](https://github.com/a-sotnikov/homework_8.2_devops/blob/main/task4_result.png)

![Nexus](https://github.com/a-sotnikov/homework_8.2_devops/blob/main/task4_nexus.png)

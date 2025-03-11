pipeline {
    agent any
    parameters {
        string(name: 'login', defaultValue: '', description: 'Ingrese el login')
        string(name: 'nameApellido', defaultValue: '', description: 'Ingrese nombre y apellido')
        string(name: 'departamento', defaultValue: '', description: 'Ingrese el departamento')
    }
    stages {
        stage('Input') {
            steps {
                script {
                    def password = sh(script: "openssl rand -base64 12", returnStdout: true).trim()
                     
                        sh sudo useradd -m -c '${nameApellido}' -d /home/${login} -s /bin/bash ${login}
                        sh echo '${login}:${password}' | sudo chpasswd
                        sh sudo chage -d 0 ${login}
                        sh echo "Usuario creado: ${login}"
                        sh echo "Contraseña temporal: ${password}"

                }
            }
        }
        
            }
        }

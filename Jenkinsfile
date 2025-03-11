pipeline {
    agent any
    parameters {
        string(name: 'login', defaultValue: '', description: 'Ingrese el login')
        string(name: 'nameApellido', defaultValue: '', description: 'Ingrese nombre y apellido')
        choice(name: 'departamento', choices: ['contabilidad', 'finanzas', 'tecnologia'], description: 'Seleccione el departamento')
    }
    stages {
        stage('Input') {
            steps {
                script {
                    def password = sh(script: "openssl rand -base64 12", returnStdout: true).trim()
                    sh """
                        sudo useradd -m -c '${nameApellido}' -d /home/${login} -s /bin/bash ${login}
                        echo '${login}:${password}' | sudo chpasswd
                        sudo chage -d 0 ${login}
                        echo "Usuario creado: ${login}"
                        echo "Contraseña temporal: ${password}"
                         """
                }
            }
        }
        
            }
        }

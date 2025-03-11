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
                     sh """
                    if [ -d /home/${login} ]; then
                        sudo rm -rf /home/${login}
                    fi
                    sudo useradd -m -c '${nameApellido}' -d /home/${login} -s /bin/bash -g ${login}
                    echo '${login}:${password}' | sudo -S chpasswd
                    sudo chage -d 0 ${login}
                    echo "Usuario creado: ${login}"
                     echo "Contraseña temporal: ${password}"
                     """

                }
            }
        }
        
            }
        }

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
                    def grupo = "${departamento}" 
                
                     
                    ''' Verificación y creación del grupo '''
                    sh """
                    if ! grep -q "^${grupo}:" /etc/group; then
                        echo "El grupo ${grupo} no existe. Creando grupo"
                        sudo groupadd ${grupo}
                    fi
                    
                    if [ -d /home/${login} ]; then
                        echo "El directorio ya existe, se eliminara para crear uno nuevo.."
                        sudo rm -rf /home/${login}
                    else 
                        echo 'generando usuario'
                    fi
                    # Crea el usuario
                    sudo useradd -m -c '${nameApellido}' -d /home/${login} -s /bin/bash -g ${grupo} ${login}
                    sleep 2
                    
                    # Se cambia la contraseña del usuario
                    echo '${login}:${password}' | sudo chpasswd
                    
                    # Se fuerza al usuario a cambiar la contrasena en su primer inicio de sesion
                    sudo chage -d 0 ${login}
                    
                    # Se indica la contraseña temportal
                    echo "Usuario creado: ${login}"
                    echo "La contraseña temporal es : ${password}"
                     """

                }
            }
        }
        
            }
        }

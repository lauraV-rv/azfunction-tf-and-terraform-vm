## Informe de laboratorio

Inicialmente se ingresó a la cuenta de Microsoft Azure mediante el comando az login, el cual permitió autenticar la sesión y habilitar el acceso a la suscripción con la que se realizaría el despliegue de la infraestructura.
Luego se trabajó sobre el repositorio proporcionado para la práctica, el cual contenía la definición de la infraestructura mediante archivos de Terraform. En estos archivos se encontraba la configuración necesaria para desplegar una Azure Function junto con los recursos asociados.

Una vez en la carpeta del proyecto, se ejecutó el comando terraform init. Este comando permitió inicializar el proyecto de Terraform, descargar el provider de Azure y preparar el entorno para interpretar correctamente los archivos .tf. Después de esto, se ejecutó terraform validate, con el fin de verificar que la sintaxis y la estructura de la configuración fueran correctas antes de proceder con el despliegue.

A continuación, se ejecutó terraform plan, comando que muestra una vista previa de los recursos que Terraform pretende crear en Azure a partir de la configuración definida. Luego, se ejecutó terraform apply, que es el comando encargado de aplicar los cambios y desplegar efectivamente la infraestructura en la nube.
<img width="1919" height="1079" alt="image (2)" src="https://github.com/user-attachments/assets/8a74cc29-f0ff-453c-acfd-372cd6320148" />

Durante este proceso se presentó un inconveniente relacionado con la región configurada para el despliegue. Inicialmente, la infraestructura no pudo crearse porque la región definida en el archivo variables.tf no estaba permitida por las políticas de la suscripción de Azure utilizada en la práctica. Para solucionar este problema, se modificó la variable location por una región válida. En este caso, se utilizó eastus2, lo que permitió continuar con el despliegue de los recursos.

Además, fue necesario cambiar el nombre de la función para evitar conflictos con un nombre que ya estaba en uso. Por esta razón, se definió un nuevo nombre para la función: azfunclau2. Con estos dos ajustes, el despliegue pudo completarse correctamente.

Una vez finalizada la ejecución de terraform apply, Terraform mostró la salida correspondiente a la URL de invocación de la función. Esta URL se genera a partir de la configuración definida en el archivo outputs.tf, y permite acceder directamente al endpoint HTTP de la Azure Function desplegada.
<img width="1919" height="1079" alt="image (4)" src="https://github.com/user-attachments/assets/40e7d10f-88bf-4e94-adc6-526040a48f22" />

Posteriormente, se probó la función accediendo a la URL generada, verificando que respondiera correctamente. Esto confirmó que la Function App se había creado con éxito y que la infraestructura configurada mediante Terraform estaba funcionando de manera adecuada.
<img width="1919" height="1020" alt="image (6)" src="https://github.com/user-attachments/assets/154f5df8-6d6d-4086-a524-bc9aea928fb5" />

Finalmente, también se verificó en el portal de Azure que los recursos se hubieran creado correctamente. Allí fue posible evidenciar la existencia del grupo de recursos, la cuenta de almacenamiento, el plan de servicio y la Function App, confirmando visualmente que el despliegue se realizó de manera exitosa.
<img width="1919" height="1022" alt="image (5)" src="https://github.com/user-attachments/assets/b0e8a09f-7a8f-4d21-b81e-ff8bd5c382dc" />
<img width="1919" height="1023" alt="image (7)" src="https://github.com/user-attachments/assets/02779cbe-bb9e-4b3c-92dd-4efdc3e38506" />

En conclusión, la práctica permitió comprender el proceso de despliegue de una Azure Function en Microsoft Azure utilizando Terraform. También evidenció la importancia de revisar cuidadosamente parámetros como la región y los nombres de los recursos, ya que estos pueden generar errores durante la creación de la infraestructura. Una vez corregidos estos aspectos, se logró desplegar la función satisfactoriamente y verificar su funcionamiento tanto desde la consola como desde el portal de Azure.

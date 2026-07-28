<div align="center">

# Universidad Politécnica Salesiana

## Sistemas Distribuidos

# Examen Final 

**Integrantes**  

Adrian Lazo

**Fecha**  
28 de julio de 2026

</div>

---

## Evidencia Inicial
### Captura 1.
App Funcionando
![alt text](images/01-app-corriendo.png)

### Captura 2. Endpoint
![alt text](images/02_local.png)

### Captura 3. Test inicial Fallando
![alt text](images/03-test.png)

---

## Reto 1 - Pruebas: la aplicación responde, pero el test falla

### Fallo Inicial
![alt text](images/03.1-inicial.png)

### Registro de qué debería responder la app:

Debería responder: ok 1 - GET / responde correctamente

**Respuesta**:

Lo que se está validando incorrectamente es el código HTTP está validando el 201, envés del 200,y  una falta de ortografía en la palabra "Aplicación" que estaba sin tilde, haciendo ese cambio, la prueba pasa.

![alt text](images/04-corregido.png)

### Prueba pasada
![alt text](images/05-pass.png)

---
## Reto 2 - Docker: imagen construida con una prueba no confiable
### Docker construye la imagen sin importar fallos
![alt text](images/06-dockerbuild.png)

### Docker no hace las pruebas porque falta RUN npm run test
![alt text](images/06-docker-sin-runtest.png)

### Dockerfile final con RUN npm run test
![alt text](images/06-docker-con-runtest.png)

### Captura o registro de un build bloqueado cuando existe una prueba fallida.
Se revertió el cambio del paso anterior, 200 a 201 para provocar el fallo.
![alt text](images/06-docker-bloqueado.png)
![alt text](images/06.1-docker-bloqueado.png)


### Captura o registro de un build exitoso cuando las pruebas pasan.
![alt text](images/06-docker-exitoso.png)


### Captura o registro del contenedor final respondiendo desde la máquina anfitriona.

![alt text](images/06-corriendo.png)
![alt text](images/06-lista.png)

---

## Reto 3 - CI/CD: el pipeline despliega sin protegerse del fallo de test

Problema encontrado, está configurado para aunque el test falle, lo muestre como exitoso aunque el deploy falle:

Por `npm test || true`

### Captura o registro del workflow inicial.
![alt text](images/07-inicial-work.png)

### Captura o registro de una ejecución donde una prueba falla.
![alt text](images/07-fallo.png)
Fallo forzado cambiando 200 por 500 en el test.

### Captura o registro que demuestre el comportamiento defectuoso inicial del pipeline.
![alt text](images/07-fail.png)
![alt text](images/07-fail.png)


### Captura o registro del workflow corregido.
![alt text](images/07-corregido.png)

### Captura o registro de una ejecución final donde las pruebas pasan y el despliegue continúa.

---

# Reto 4 - Kubernetes: despliegue validado con prueba de disponibilidad

### Captura o registro de la aplicación del manifiesto.
![alt text](images/08-inicial.png)
![alt text](images/08-manifiesto.png)

### Captura o registro de los pods en ejecución.

Pods en ejecución, son los más jóvenes
![alt text](images/08-pods.png)

### Captura o registro del Service y sus endpoints asociados.
![alt text](images/image.png)
![alt text](images/08-endpoints.png)


### Captura o registro de una petición exitosa a la aplicación a través del servicio.
![alt text](images/08-probar.png)
![alt text](images/08-probar-ok.png)

### Captura o registro de una modificación controlada del test o de la app que demuestre que el pipeline detecta fallos reales.
![alt text](images/08-controlado.png)



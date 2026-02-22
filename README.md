# postman-api-testing-practice Pruebas automatizadas y JSONPlaceholder

# Proyecto de Pruebas de API con Postman 🚀

Este repositorio contiene una colección de Postman diseñada para probar los endpoints de una API REST (JSONPlaceholder).

## 🧠 Lo que aprendí y solucioné:

### 1. Manejo de Status Codes (200 vs 201)
* **Error encontrado:** El test fallaba porque esperaba un código `200 OK`, pero la API devolvía un `201 Created`.
* **Solución:** Ajusté el script de validación para aceptar el código `201`, que es el estándar correcto cuando se crea un recurso nuevo con un método **POST**.

### 2. Resolución de "Undefined" en JavaScript
* **Error encontrado:** `AssertionError: expected undefined to deeply equal 1`. 
* **Causa:** Intentaba acceder a los datos sin haber convertido primero la respuesta del servidor en un objeto JSON.
* **Solución:** Implementé la línea `var jsonData = pm.response.json();` para mapear la respuesta antes de la aserción.

### 3. Validación Dinámica de Datos
* **Error encontrado:** El ID esperado era `1`, pero el servidor generaba el `101`.
* **Mejora de QA:** Cambié la validación rígida (Hardcoding) por una validación de tipo:
  ```javascript
  pm.expect(jsonData.id).to.be.a('number');
  

# Mejora de Seguridad en Dependencias

## 1. Problemas de seguridad y soluciones
El archivo original solo tenía los nombres de las librerías. Esto es peligroso porque:
- **Falta de integridad:** Alguien podría hackear el repositorio de librerías y cambiar el código.
- **Inestabilidad:** Una actualización imprevista podría romper la aplicación.

**Solución:** He aplicado **Version Pinning** (fijar la versión exacta) y **Hashing** (verificar la firma digital del archivo). Además, he diferenciado entre el **Input File** (lo que yo pido) y el **Lock File** (el `requirements.txt` generado con hashes que garantiza que siempre se instale lo mismo).

## 2. Procedimiento de actualización en producción
Para el futuro, recomiendo:
1.  **Entorno de Staging:** Probar las actualizaciones en un entorno espejo antes de ir a producción.
2.  **Uso de herramientas:** Ejecutar `pip-audit` para detectar fallos antes de subir cambios.
3.  **Pipeline de CI:** El archivo con hashes debe ser verificado automáticamente por el sistema de integración continua.

## 3. Escenarios que prevenimos
- **Dependency Hijacking:** Que instalemos un virus porque el autor de una librería fue hackeado.
- **Breaking Changes:** Que la app deje de funcionar un lunes por la mañana porque una librería se actualizó sola.
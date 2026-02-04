# Escaneo de Vulnerabilidades y Alternativas

## 1. GitHub Dependabot
He configurado **Dependabot** en este repositorio siguiendo estos pasos:
1. En GitHub: `Settings` -> `Code security and analysis`.
2. Activar `Dependency graph`, `Dependabot alerts` y `Dependabot security updates`.
Esto permite que GitHub me avise y cree correcciones automáticas si alguna librería tiene un fallo de seguridad conocido (CVE).

## 2. Alternativas para Nube Privada (Self-hosted)
Si no usáramos GitHub, propongo estas 3 alternativas:

| Herramienta | Pros | Contras |
| :--- | :--- | :--- |
| **Snyk** | Interfaz excelente y gran base de datos de fallos. | La versión gratuita es limitada. |
| **OWASP Dependency-Check** | Es el estándar gratuito y de código abierto. | Puede dar más falsos positivos. |
| **Renovate** | El mejor para automatizar actualizaciones de versiones. | Requiere configuración más técnica. |

**Elección:** Recomiendo **OWASP Dependency-Check** por ser la opción más sólida y gratuita para entornos privados, con una comunidad enorme detrás.

## Resultados del escaneo de Dependabot
Tras activar la herramienta, se han detectado **6 vulnerabilidades** en la librería Django:
- **3 de nivel Alto:** Problemas de SQL Injection.
- **3 de nivel Bajo:** Problemas de complejidad algorítmica y discrepancias de tiempo.

**Acción tomada:** Es necesario actualizar Django a una versión parcheada (por ejemplo, la 6.0.1 o superior si estuviera disponible) para mitigar estos riesgos.
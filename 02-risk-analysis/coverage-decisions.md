# Decisiones de Cobertura

## Riesgos que se probarán primero
1. **R1 - Validacion de Stock existente:** Pruebas de integración entre Checkout y confirmación de BD.
2. **R2 - Errores en pantalla:** Validaciones cruzadas de Endpoints API vs interfaz Web.
3. **R3 - Falta de autenticacion:** Pruebas funcionales de autenticación, logout y manejo de sesión.

## ¿Por qué esos riesgos son prioridad?
Estos riesgos requieren atención prioritaria al comprometer directamente los ingresos (conversión y pagos), la consistencia del inventario y la seguridad del sistema. Aplicar un testing orientado a riesgos financieros mitiga incidentes de alto impacto antes de su salida a producción.

## Qué se probará menos o quedará fuera por ahora
- **Pruebas de Seguridad y Control de Acceso en la API:** Pruebas en dispositivos o pantallas antiguas.
- **Validar Stock disponible:** Navegación exploratoria no transaccional.
- **Manejo de stock comprometido (reservas):** Enfocadas solo a flujos CRUD funcionales en esta fase.

# Justificación de exclusiones

Justificación: Las pruebas no funcionales de volumen masivo se posponen para etapas posteriores, dando prioridad a la corrección de riesgos funcionales y de seguridad críticos en los endpoints y procesos clave.
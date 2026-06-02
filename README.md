# Landing Page - Tecnología G3 (Estratek)

Landing page optimizada y reestructurada para Tecnología G3 de Estratek con enfoque en captación de leads B2B y registro a eventos directivos.

## Novedades y Actualizaciones (Versión Actual)

Aquí detallamos los principales cambios e implementaciones de esta versión:

### 1. Embudo de Conversión Reestructurado
* **Foco en Demos**: El formulario principal de la landing ahora está 100% orientado a agendar demostraciones de la plataforma Tecnología G3.
* **Integración con Google Sheets**: Los datos de contacto del formulario se envían automáticamente en tiempo real a una hoja de cálculo centralizada de Google Sheets utilizando un script AJAX (`fetch`) conectado a Google Apps Script.
* **Sección de Recursos**: Se integró un hub de recursos con acceso al blog corporativo y el video explicativo de YouTube de Estratek.

### 2. Sección de Desayuno Ejecutivo C-Level Exclusivo
* **Enfoque de 1 Evento**: Se redujo el bloque a un solo evento principal destacado para maximizar conversiones y evitar la sobrecarga de un calendario múltiple.
* **Interactividad**: Tanto la imagen del flyer (`desayuno-sostenibilidad.jpg`) como el botón principal están vinculados al registro en Luma (`https://luma.com/pzo9bbo1`).
* **Ubicación Estratégica**: Colocada inmediatamente debajo de la Trayectoria y sobre el Triángulo de la Sostenibilidad para captar la atención de directivos de inmediato.
* **Espaciado Optimizado**: Reducción de márgenes y padding para un flujo de lectura compacto.

### 3. Ajustes de Paleta y Branding
* **Celeste TG3 como Primario**: Botones de llamada a la acción (CTAs) y foco de entradas utilizan el celeste oficial de Tecnología G3 (`#399ab1`).
* **Magenta Minimalista**: El rosado/magenta (`#df1a69`) se restringe únicamente a acentos y destaques sutiles de interfaz.
* **Navegación e Inicio de Sesión**: Se redirigió el enlace "Iniciar Sesión" del nav bar a la URL oficial de la app (`https://app.estratek.com/login`).

### 4. Limpieza y Optimización
* **Corrección de Bugs**: Corrección del bloqueo de scroll vertical provocado por etiquetas de navegación no cerradas.
* **Eliminación de Testimonios**: Remoción de secciones redundantes para agilizar la carga del sitio.

---

## Archivos de Configuración Incluidos
* **[index.html](index.html)**: Código fuente de la Landing Page.
* **[google_sheets_setup.md](google_sheets_setup.md)**: Guía paso a paso y código de Google Apps Script para configurar el webhook del formulario de Leads en tu Google Drive.

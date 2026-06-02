# Integración de Google Sheets para el Formulario de Demo (Estratek TG3)

Para conectar el formulario de agendamiento de demo de la Landing Page con un Google Sheet en tu Google Drive sin necesidad de servidores o servicios de pago, sigue estos sencillos pasos:

---

## Paso 1: Crear el Google Sheet
1. Ve a [Google Sheets](https://sheets.new) en tu navegador para crear una nueva hoja de cálculo.
2. Nombra el archivo a tu gusto (por ejemplo: `Leads - Demo Tecnología G3`).

## Paso 2: Abrir Apps Script y Pegar el Código
1. En el menú superior de tu hoja de cálculo, haz clic en **Extensiones > Apps Script**.
2. Borra cualquier código existente en el editor de Apps Script.
3. Copia y pega el siguiente código:

```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  
  if (!e || !e.postData || !e.postData.contents) {
    return ContentService.createTextOutput(JSON.stringify({status: "error", message: "No data received"}))
      .setMimeType(ContentService.MimeType.JSON);
  }
  
  try {
    var data = JSON.parse(e.postData.contents);
    
    // Crea encabezados automáticamente en la primera fila si la hoja está vacía
    if (sheet.getLastRow() === 0) {
      sheet.appendRow(["Fecha", "Nombre", "Apellido", "Correo Corporativo", "Nombre de la Empresa", "Cargo", "Sede"]);
    }
    
    // Inserta los datos del cliente potencial
    sheet.appendRow([
      data.Fecha || new Date().toLocaleString("es-ES"),
      data.Nombre,
      data.Apellido,
      data.Correo,
      data.Empresa,
      data.Cargo,
      data.Sede
    ]);
    
    return ContentService.createTextOutput(JSON.stringify({status: "success"}))
      .setMimeType(ContentService.MimeType.JSON);
  } catch (error) {
    return ContentService.createTextOutput(JSON.stringify({status: "error", message: error.toString()}))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

4. Haz clic en el botón de **Guardar** (icono de disquete).

## Paso 3: Publicar el Apps Script como Web App
1. En la esquina superior derecha del editor de Apps Script, haz clic en **Implementar > Nueva implementación**.
2. Haz clic en el engranaje de configuración junto a "Seleccionar tipo" y elige **Aplicación web**.
3. Configura los parámetros:
   - **Descripción:** `Integración formulario TG3 Estratek`
   - **Ejecutar como:** `Tu cuenta de Google (Tu correo)`
   - **Quién tiene acceso:** `Cualquier persona` (Esto es obligatorio para que el formulario frontend pueda enviar los datos sin pedir inicio de sesión).
4. Haz clic en **Implementar**.
5. Si te pide otorgar accesos, haz clic en **Autorizar acceso**, selecciona tu cuenta de Google, haz clic en **Advanced (Configuración avanzada)** y luego en **Go to... (Ir a...)** para permitir que el script escriba en tu Google Sheet.
6. Copia la **URL de la aplicación web** que se generará (debe verse similar a `https://script.google.com/macros/s/AKfycb.../exec`).

## Paso 4: Configurar la URL en el Código
1. Abre tu archivo `index.html`.
2. Busca la línea que contiene:
   ```javascript
   const SCRIPT_URL = "https://script.google.com/macros/s/AKfycbz_TU_URL_DE_APPS_SCRIPT/exec";
   ```
3. Reemplaza `"https://script.google.com/macros/s/AKfycbz_TU_URL_DE_APPS_SCRIPT/exec"` con la URL de tu aplicación web copiada en el paso anterior.
4. Guarda el archivo y realiza una prueba enviando el formulario en **[http://localhost:8080](http://localhost:8080)**. Los leads aparecerán en tiempo real en tu hoja de cálculo.

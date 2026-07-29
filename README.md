# Formulario de Contacto

## Código original (enviar.php)

**Nombre del archivo:** `enviar.php`
**Ubicación original:** `/FormContac/htdocs/enviar.php`

```php
<?php

// Llamando a los campos
$nombre = isset($_POST['nombre']) ? trim($_POST['nombre']) : '';
$correo = isset($_POST['correo']) ? trim($_POST['correo']) : '';
$telefono = isset($_POST['telefono']) ? trim($_POST['telefono']) : '';
$mensaje = isset($_POST['mensaje']) ? trim($_POST['mensaje']) : '';

if ($nombre === '' || $correo === '' || $mensaje === '') {
    header('Location: mensaje-de-error.html');
    exit;
}

// Datos para el correo
$destinatario = "jmoplis@outlook.com";
$asunto = "Contacto desde nuestra web";

$carta = "De: $nombre \n";
$carta .= "Correo: $correo \n";
$carta .= "Telefono: $telefono \n";
$carta .= "Mensaje: $mensaje";

// Enviando Mensaje
$envioExitoso = mail($destinatario, $asunto, $carta);

if ($envioExitoso) {
    header('Location: mensaje-de-envio.html');
    exit;
}

header('Location: mensaje-de-error.html');
exit;

?>
```

**Nota:** Para usar este PHP se necesita un hosting con PHP y un MTA configurado (sendmail, postfix, etc.). En GitHub Pages no funciona porque no ejecuta PHP.

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Enviar correo diario</title>
  <style>
    body, html {
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #f4f6f9;
    }
    .container {
      text-align: center;
      padding: 2rem;
      background: #ffffff;      
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      width: 400px;
    }
    h1 {
      color: #0a66c2;
      font-size: 1.8rem;
      margin-bottom: 20px;
    }
    p {
      font-size: 1rem;
      color: #555;
      margin-bottom: 30px;
      line-height: 1.5;
    }
    button {
      padding: 12px 30px;
      font-size: 1.1rem;
      font-weight: 600;
      color: white;
      background-color: #0a66c2;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      transition: all 0.3s ease;
      width: 100%;
    }
    button:hover {
      background-color: #084d97;
      box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
      transform: translateY(-2px);
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Reporte de Pedidos</h1>
    <p>Haz clic para enviar el correo con la solicitud de material y papel troquelado.</p>
    <button id="abrirCorreo">Generar Solicitud de Material</button>
  </div>

  <script>
    const hoy = new Date();
    const dd = String(hoy.getDate()).padStart(2, '0');
    const mm = String(hoy.getMonth() + 1).padStart(2, '0');
    const yyyy = hoy.getFullYear();
    const fecha = `${dd}/${mm}/${yyyy}`;

    // --- CONFIGURACIÓN DEL MENSAJE ---
    const destinatario = "cocinars@glocoquality.com";
    const asunto = `Solicitud de Material - ${fecha}`;
    const cuerpo = `Hola,%0D%0A%0D%0APor favor, solicitamos el envío del papel troquelado correspondiente a esta fecha: ${fecha}.%0D%0A%0D%0AUn saludo.`;
    // ---------------------------------

    document.getElementById('abrirCorreo').onclick = () => {
      const url = `https://outlook.office.com/mail/deeplink/compose?to=${destinatario}&subject=${encodeURIComponent(asunto)}&body=${cuerpo}`;
      window.open(url, '_blank');
    };
  </script>

</body>
</html>

<script>
  import maleta from '../assets/img_maleta.png';
</script>

<main>
  <!-- Descripción del producto -->
  <h1>CCTV FULL HD</h1>
  <p>Cctv Equipo video de buceo 2, 3 o 4 buzos. <br>Equipo robusto, compacto y de fácil manejo.<br> Pensado y diseñado por buceadores que conocen las necesidades y las complicaciones del buceo comercial.</p>

  <!-- Contenedor para la maleta y las características -->
  <div class="maleta-caracteristicas-container">
    <!-- Imagen de la maleta con características -->
    <div class="maleta-container">
      <img src={maleta} alt="maleta" class="maleta" title="Características:
      - Transmisión de larga distancia
      - Sistema operativo potente
      - Mejora de visión en agua sucia
      - Dual Cam
      - Dual monitor
      - Compatibilidad y adaptabilidad
      - Opciones de alimentación flexibles
      - Opcional batería interna de emergencia
      - Tamaño personalizable" />
    </div>

    <!-- Características -->
    <div class="caracteristicas">
      <ul>
        <li><strong>Transmisión de larga distancia:</strong> Capacidad de transmitir datos hasta una profundidad de 1000 metros, lo que permite a los buceadores explorar áreas remotas sin perder la conexión.</li>
        <li><strong>Sistema operativo potente:</strong> Equipado con un sistema operativo potente que permite gestionar cámaras de hasta 8 megapíxeles, ofreciendo una calidad superior de imagen y un zoom sin pixelar la imagen. Además, el sistema mejora digitalmente la imagen para obtener resultados óptimos incluso en condiciones de visibilidad reducida o agua sucia.</li>
        <li><strong>Mejora de visión en agua sucia:</strong> Tecnología avanzada que mejora la visión en agua sucia, proporcionando una experiencia visual clara y nítida para los buceadores.</li>
        <li><strong>Dual Cam:</strong> Función dual cam que permite alternar entre una cámara montada en el casco (helmet cam) y una cámara de mano (hand cam), brindando flexibilidad para capturar diferentes ángulos y perspectivas bajo el agua.</li>
        <li><strong>Dual monitor:</strong> Sistema equipado con dual monitor que permite a los buceadores ver diferentes canales en monitores separados, con opciones de conexión VGA y HDMI para una mayor versatilidad.</li>
        <li><strong>Compatibilidad y adaptabilidad:</strong> Totalmente adaptable a todos los umbilicales y con conectores personalizables para satisfacer las necesidades específicas de cada buceador.</li>
        <li><strong>Opciones de alimentación flexibles:</strong> Puede ser alimentado por una batería externa de 12V o mediante una fuente de alimentación AC-DC de 100/220V, lo que garantiza un rendimiento óptimo en cualquier entorno submarino.</li>
        <li><strong>Opcional batería interna de emergencia:</strong> Disponible una opción de batería interna de emergencia para proporcionar energía adicional en situaciones críticas.</li>
        <li><strong>Tamaño personalizable:</strong> Diseño adaptable y personalizable para satisfacer las necesidades específicas de los buceadores, proporcionando comodidad y funcionalidad en cada inmersión.</li>
      </ul>
    </div>
  </div>

  <h3>Con estas características innovadoras, este sistema tecnológico ofrece una solución integral para mejorar la experiencia de buceo, <br>permitiendo a los usuarios capturar imágenes de alta calidad, transmitir datos de manera eficiente y disfrutar de una visualización clara y nítida bajo el agua.</h3>
</main>

<style>
  main {
    position: relative;
    background-color: rgba(0, 0, 0, 0.7);
    padding: 60px;
    text-align-last: auto;
    overflow-y: auto; /* Habilita el scroll vertical */
  }
  

  h1 {
    margin-left: 380px;
    font-size: 24px;
    color: #FFFBFB; 
  }

  h3 {
    margin-top: 50px;
    text-align: center;
    color: goldenrod;
  }

  p {
    margin-left: 380px;
    font-size: 16px;
    line-height: 1.6;
    color: #FFFFFF; 
    margin-bottom: 10px; 
  }

  /* Estilos para la maleta */
  .maleta-caracteristicas-container {
    display: flex;
    align-items: flex-start;
  }

  .maleta {
    width: 350px; /* Ajusta el tamaño según sea necesario */
    height: auto;
    cursor: pointer;
  }

  .maleta-container {
    margin-right: 20px; /* Espacio entre la maleta y las características */
  }

  .caracteristicas {
    flex-grow: 1; /* Para que las características ocupen todo el espacio disponible */
    color: white;
    font-size: 16px;
    padding: 10px;
  }

  .maleta:hover::after {
    content: attr(title);
    position: absolute;
    top: calc(100% + 10px); /* Posiciona el texto debajo de la imagen */
    left: 0;
    width: 100%;
    height: 100%¡;
    padding: 10px;
    background-color: rgba(0, 0, 0, 0.7);
    color: white;
    font-size: 14px;
    font-weight: bold;
    white-space: pre-line; /* Permite mostrar saltos de línea */
  }


  ul {
    margin-top: 20px;
    list-style-type: none;
  }

  strong {
    font-size: 18px;
    color: goldenrod;
  }

  @media (max-width: 768px) {
    .maleta-caracteristicas-container {
      flex-direction: column; /* Cambia a columna en dispositivos móviles */
    }

    .maleta-container {
      margin-right: 0; /* Elimina el margen entre la maleta y las características en dispositivos móviles */
      margin-bottom: 20px; /* Espacio entre la maleta y las características en dispositivos móviles */
    }
  }
</style>

<script>
    let nombreComentarista = '';
    let comentario = '';
    let comentarios = [];
    let imagenUrl = 'https://metricool.com/wp-content/uploads/PERFIL-TIKTOK-scaled.jpg';
    
    function manejarEnviar() {
      if (nombreComentarista.trim() && comentario.trim()) {
        comentarios = [...comentarios, { nombre: nombreComentarista, comentario }];
        // Vaciar los inputs después de enviar un comentario
        nombreComentarista = '';
        comentario = '';
      }
    }
  </script>
  
  <style>
    .tarjeta-presentacion {
      background-color: #f0f0f0; /* Color de fondo de la tarjeta de presentación */
      border: 1px solid #ccc;
      padding: 10px;
      margin-top: 20px;
      display: flex;
      flex-direction: row; /* Elementos en fila */
      justify-content: space-between; /* Distribuye los elementos horizontalmente */
      align-items: center; /* Centra verticalmente */
      max-width: 400px; /* Ancho máximo de la tarjeta */
    }
  
    .tarjeta-presentacion img {
      max-width: 60px; /* Ajusta el ancho máximo de la imagen */
      border-radius: 50%; /* Da un borde redondeado a la imagen */
    }
  
    .informacion {
      flex-grow: 1; /* Hace que ocupe el espacio restante */
      margin-left: 20px; /* Margen a la izquierda de la información */
    }
  
    .informacion p {
      margin: 0;
    }
  
    .informacion input,
    .informacion textarea,
    .informacion button {
      margin-top: 10px;
    }
  
    /* Estilo para los comentarios */
    .comentario {
      background-color: #e0e0e0; /* Color de fondo del comentario */
      border: 1px solid #ccc;
      padding: 10px;
      margin-top: 10px; /* Espaciado superior entre comentarios */
      max-width: 400px; /* Ancho máximo del comentario */
    }
  </style>
  
  <!-- Contenido de la tarjeta -->
  <div class="tarjeta-presentacion">
    <!-- Imagen de perfil -->
    <img src={imagenUrl} alt="Imagen de perfil" />
  
    <!-- Información -->
    <div class="informacion">
      <p>Nombre Completo: Paul Ávila Rodríguez</p>
      <p>Título: Desarrollador Web</p>
      <p>Habilidades: HTML, CSS, JavaScript</p>
    </div>
  </div>
  
  <!-- Formulario de comentarios -->
  <form on:submit|preventDefault={manejarEnviar} class="informacion">
    <label>
      Nombre:
      <input type="text" bind:value={nombreComentarista} />
    </label>
    <label>
      Comentario:
      <textarea bind:value={comentario}></textarea>
    </label>
    <button type="submit">Enviar</button>
  </form>
  
  <!-- Comentarios existentes -->
  {#if comentarios.length > 0}
    {#each comentarios as { nombre, comentario }, index}
      <div class="comentario">
        <p>Comentario de {nombre}:</p>
        <p>{comentario}</p>
      </div>
    {/each}
  {/if}
  
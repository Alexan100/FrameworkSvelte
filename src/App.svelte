<script>
	//Importamos la carpeta creada "components", junto con el archivo Navbar, este es el cabecero 
import Navbar from './components/Navbar.svelte';
//Importamos la carpeta creada "components", junto con el archivo Tarea, este es el proyecto en si.
import Tarea from './components/Tarea.svelte'
</script>


<!-- Es el contenido principal con todos sus componetes -->
<main class="fondo">
	<!--Mandamos a llamar los archivos importados -->
	<Navbar />
<Tarea />
	</main>

<style>
	/* Cambiamos estilos a la interfaz con la clase asignada */
	.fondo{
		background-image: linear-gradient(to bottom right, #0033CC, #7797ff, #41ddf1);
		height: 100vh;
		
	}

	
</style>
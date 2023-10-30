<script>
    //Crearemos unas variables tareas y nombreTarea, para asignar las funciones necesarias
    let tareas = [];
    let nombreTarea = '';

// Creamos una funcion con un evento llamado "agregarTarea", el cual dara accion cuando el usuario de click
//para poder agregar tareas
    function agregarTarea(event){
        if(event.key === 'Enter'){

            const tarea = {
                nombre: nombreTarea,
                estado: false
            }
            tareas.push(tarea);
            console.log(tareas);
            tareas = tareas;
            nombreTarea = '';
        }
    }

    function deleteTarea(i){
        tareas.splice(i, 1);
        tareas = tareas;
    }

    function actualizarTarea(tarea, i){
        tareas[i].estado = !tarea.estado
    }
</script>

<div>
    <!--Craeremos un div con su clase ya asignada con su estilo de la libreria boostrap -->
   <div class="container mt-5">
    <!--Craemos otro div con su clase asignada para poder dar estilo y centralizacion -->
       <div class="row">
        <!-- Creamos otro div co su clase-->
           <div class="col-lg-8 offset-lg-2">
            <!-- Creamos un input tipo text con sus clases, para poder agregar aqui las tareas -->
              <input type="text" class="form-control form-control-lg"
                    on:keydown={agregarTarea}
                    bind:value={nombreTarea}    
                    placeholder="Ingresar tarea..">
              <br>
            </div>
           
           <div class="col-lg-6 offset-lg-3">
               {#if tareas.length === 0}
               <div class="card p-2">
                   <h6>No hay tareas para mostrar mi brother...</h6>
               </div>
               {/if}

               <ul class="list-group">
                {#each tareas as tarea, i}
                   <li class="list-group-item d-flex justify-content-between">
                       <!-- svelte-ignore a11y-click-events-have-key-events -->
<span class={tarea.estado === true ? 'text-success cursor' : 'cursor'} on:click={() => actualizarTarea(tarea, i)}>
                           <i class={tarea.estado === true ? 'fas fa-check-circle' : 'far fa-circle'} ></i>
                       </span>
                        <h5>{ tarea.nombre }</h5>
                        <!-- svelte-ignore a11y-click-events-have-key-events -->
                        <span class="cursor text-danger" on:click={() => deleteTarea(i)}>
                            <i class="fas fa-trash-alt"></i>
                        </span>
                   </li>
                   {/each}
               </ul>
           </div>
       </div>
   </div>
</div>

<style>
    .form-control-lg {
        font-size: 1.8rem;
    }
    input {
        text-align: center;
    }

    .cursor {
        cursor: pointer;
    }
</style>
<script>
    let tareas = [];
    let nombreTarea = "";
    // function agregarTarea(e) {
    //     //console.log(e);
    //     if (event.key === "Enter") {
    //         tareas = [...tareas, nombreTarea];
    //         console.log(tareas);
    //         nombreTarea = "";
    //     }
    // }
    const agregarTarea = (e) => {
        if (e.key === "Enter") {
            const tarea = {
                nombre: nombreTarea, 
                estado: false
            }
            tareas = [...tareas, tarea];
            console.log(tareas);
            nombreTarea = "";
        }
    };

    const deleteTarea = (i) => {
        tareas.splice(i, 1);
        tareas = tareas;
    }

    const cambiarEstado = (i) => {
        tareas[i].estado = !tareas[i].estado;
    }
</script>

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

<div class="container">
    <div class="row my-5">
        <div class="col-12">
            <input
                type="text"
                class="form-control form-control-lg"
                on:keydown={agregarTarea}
                bind:value={nombreTarea}
                placeholder="Insertar tarea" />
        </div>
    </div>
    <div class="row">
        <div class="col-12">
            {#if tareas.length == 0}
            <div class="card p-2 text-center">
                <h5>No hay tareas para mostrar</h5>
            </div>
            {:else}
            <ul class="list-group">
                {#each tareas as tarea, i}
                <li class="list-group-item d-flex justify-content-between align-items-center">
                    <span class="cursor" on:click={() => cambiarEstado(i)}><i class={tarea.estado ? "fas fa-check-circle fa-2x text-success" : "far fa-circle fa-2x" }></i>
                    </span>
                    <h3>{tarea.nombre}</h3>
                    <span class="cursor text-danger" on:click={() => deleteTarea(i)}>
                        <i class="fas fa-trash-alt fa-2x"></i>
                    </span>
                </li>
                {/each}
                
            </ul>
            {/if}
       </div>
    </div>
</div>

<script>
    let List = [];
    let nuevaTarea;
    let i = 0;
    let bool = false;

    function agregarTarea() {
        if(nuevaTarea){
            List = [...List, {id:i+=1, texto:nuevaTarea, seleccion:false}];
        }
        else{
            alert("Escribe una tarea")
        }
        nuevaTarea = "";
    }


    function revisionCheck(id) {
        const tarea = List.find(item => item.id === id);
        tarea.seleccion = !tarea.seleccion;
    }

</script>

<main>
    <section class="container left">
        <div class="formContainer">
            <h1>To Do List</h1>
            <form action="">
                <label for="task"><input type="text" id="task" placeholder="Add Task" bind:value={nuevaTarea}><button class="addButton" type="button" on:click={agregarTarea}>Add</button></label>
            </form>
            <div class="listContainer">
                {#if List.length > 0}
                <ul>
                    {#each List as tarea}
                        {#if !tarea.seleccion}
                            <div class="tareaContainer"><input type="checkbox" name="" id="" bind:checked={tarea.seleccion} on:change={revisionCheck(tarea.id)} ><li>{tarea.texto}</li></div>
                        {/if}
                    {/each}
                </ul>
                {:else}
                <p>No hay tareas.</p>
                {/if}
            </div>
        </div>
    </section>
    <section class="container right">
        <div class="formContainer">
            <h1>Completed</h1>
            <div class="listContainer">
                {#if List.length > 0}
                    <ul>
                        {#each List as completed}
                            {#if completed.seleccion}
                                <div class="tareaContainer"><input type="checkbox" name="" id="" bind:checked={completed.seleccion} on:change={revisionCheck(completed.id)}><li>{completed.texto}</li></div>
                            {/if}
                        {/each}
                    </ul>
                {:else}
                    <p>No hay tareas.</p>
                {/if}
            </div>
        </div>
    </section>
</main>

<style>
    *{
        box-sizing: border-box;
    }

    main{
        font-family: Helvetica, sans-serif;
        background-color: #0f132e;
        width: 100vw;
        height: 100vh;
        display: flex;
        color: #fff;
    }

    h1{
        font-size: 2.3em;
    }

    li{
        margin: 10px;
    }

    ul{
        list-style: none;
    }

    label{
        width: 100%;
        display: flex;
        justify-content: center;
    }

    label input{
        width: 80%;
        font-size: 1.3em;
        border-radius: 10px 0 0 10px;
        padding: 5px;
        border: 0;
    }

    .container{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 100%;
    }

    .formContainer{
        background-color: #19274e;
        width: 70%;
        height: 60%;
        padding: 40px;
        border-radius: 15px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        min-width: 500px;
        max-width: 550px;
    }

    .listContainer{
        width: 100%;
        height: 60%;
        background-color: #0f132e;
        margin: 20px 0;
        overflow-y: scroll;
        border-radius: 15px;
    }

    .addButton{
        height: 100%;
        margin: 0;
        padding: 5px;
        width: 20%;
        background-color: #f7a21b;
        border: 0;
        border-radius: 0 10px 10px 0;
        font-size: 1.3em;
    }


    .addButton:hover{
        cursor: pointer;
        scale: .9;
        border-radius: 10px;
    }

    .tareaContainer{
        display: flex;
    }

</style>


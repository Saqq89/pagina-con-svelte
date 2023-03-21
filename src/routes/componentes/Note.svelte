<script>
    export let title;
    export let color;
    export let text;
    export let id;

    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    function handleChange(){
        dispatch('update', {
            id: id,
            text: text,
            color: color,
            title: title
        });
    }

    function handleColor(){
        dispatch('color', {
            id: id
        });
    }

    function handleRemove(){
        dispatch('remove', {
            id: id
        });
    }
</script>

<div class="Note">
    <div class="Note-container" style={' background-color: ' + color}>
        <div class="header">
            <div class="options">
                <button on:click={handleColor}><svg xmlns="http://www.w3.org/2000/svg" height="24" width="24"><path d="M12 21.95q-2.05 0-3.862-.787-1.813-.788-3.163-2.138-1.35-1.35-2.137-3.162Q2.05 14.05 2.05 12q0-2.075.8-3.887.8-1.813 2.175-3.163Q6.4 3.6 8.25 2.825q1.85-.775 3.925-.775 2 0 3.763.687 1.762.688 3.1 1.888 1.337 1.2 2.125 2.85.787 1.65.787 3.575 0 2.825-1.7 4.4-1.7 1.575-4.225 1.575h-1.65q-.25 0-.363.138-.112.137-.112.312 0 .3.338.837.337.538.337 1.263 0 1.1-.675 1.737-.675.638-1.9.638ZM12 12Zm-5.35.925q.625 0 1.025-.4.4-.4.4-1.025 0-.625-.4-1.025-.4-.4-1.025-.4-.625 0-1.025.4-.4.4-.4 1.025 0 .625.4 1.025.4.4 1.025.4Zm2.925-3.9q.625 0 1.025-.4.4-.4.4-1.025 0-.625-.4-1.025-.4-.4-1.025-.4-.6 0-1.013.4-.412.4-.412 1.025 0 .625.412 1.025.413.4 1.013.4Zm4.875 0q.6 0 1.013-.4.412-.4.412-1.025 0-.625-.412-1.025-.413-.4-1.013-.4-.625 0-1.025.4-.4.4-.4 1.025 0 .625.4 1.025.4.4 1.025.4Zm2.875 3.9q.625 0 1.025-.4.4-.4.4-1.025 0-.625-.4-1.025-.4-.4-1.025-.4-.6 0-1.013.4-.412.4-.412 1.025 0 .625.412 1.025.413.4 1.013.4Zm-5.35 6.875q.2 0 .325-.112.125-.113.125-.313 0-.35-.363-.813Q11.7 18.1 11.7 17.2q0-1.075.725-1.7t1.8-.625h1.8q1.65 0 2.713-.937Q19.8 13 19.8 11.075q0-2.95-2.262-4.913Q15.275 4.2 12.175 4.2q-3.3 0-5.638 2.275Q4.2 8.75 4.2 12q0 3.225 2.275 5.512 2.275 2.288 5.5 2.288Z"/></svg></button>
                <button on:click={handleRemove}><svg xmlns="http://www.w3.org/2000/svg" height="24" width="24"><path d="M7 20.95q-.875 0-1.512-.625Q4.85 19.7 4.85 18.8V6.15h-1.1V4H8.9V2.9h6.2V4h5.175v2.15h-1.1V18.8q0 .9-.637 1.525-.638.625-1.513.625Zm10.025-14.8H7V18.8h10.025Zm-8 10.75h2V8.025h-2Zm3.975 0h2V8.025h-2ZM7 6.15V18.8Z"/></svg></button>
            </div>
        </div>

        <div class="content">
            <div class="title">
                <input type="text" placeholder="Sin titulo..." bind:value={title} on:change={handleChange}>
            </div>
            <div class="text">
                <textarea bind:value={text} 
                    cols="30" 
                    rows="10" 
                    placeholder="Escribir..." 
                    on:change={handleChange}></textarea>
            </div>
        </div>
    </div>
</div>

<style>
    .Note{
        background-color: white;
        border-radius: 3px;
        border: solid 2px transparent;
        overflow: hidden;
        height: 400px;
    }

    .Note-container{
        height: 100%;
    }

    .Note:focus-within{
        border: solid 2px ;
        box-shadow: inset 0 3px 6px rgba(0,0,0,0.16), 0 4px 6px rgba(0,0,0,0.45);
    }

    .Note .Note-container .header{
        padding: 5px;
    }

    .header .options {
        display: flex;
        justify-content: space-between;
    }

    .Note .content{
        padding: 0 20px;
    }

    .text textarea{
        width: 100%;
        border: 0;
        outline: none;
        resize: none;
        height: 250px;
    }

    .title input{
        font-size: 22px;
        font-weight: bold;
        padding: 10px 0;
        outline: none;
        border: none;
        width: 100%;
    }

    button{
        margin: 0;
        border: none;
        background-color: transparent;
        cursor: pointer;
    }

    textarea, input{
        background: transparent;
    }

    button svg{
        fill: rgba(0, 0, 0, 0.3);
    }

    button:hover svg{
        fill: black;
    }

</style>
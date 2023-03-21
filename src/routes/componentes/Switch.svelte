<script>
    import { darkmode } from '../store/store.js';

    function handleClick(){
        darkmode.update(darkmode => !darkmode);
    }
</script>

<div class="Switch">
    <div class="switch-container">
        <button class="circle" on:click={handleClick}></button>
    </div>
    {$darkmode}
</div>

<style>
    .switch-container{
        background-color: #ccc;
        width: 50px;
        height: 25px;
        border-radius: 30px;
        margin: 0 10px;
    }

    .switch-container .circle{
        cursor: pointer;
        width: 25px;
        height: 25px;
        border-radius: 50%;
        transition: all 0.2s;
    }
</style>
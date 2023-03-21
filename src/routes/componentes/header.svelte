<script>
    import Logo from './Logo.svelte'
    import Search from './Search.svelte'
    import Settings from './Settings.svelte'
</script>

<div class="Header">
    <Logo appName='Notas'/>

    <Search on:input />

</div>

<style>
    .Header{
        border-bottom: solid 1px #ccc;
        display: flex;
        align-items: center;
        align-content: center;
        justify-content: space-between;
        padding: 10px;
    }
</style>
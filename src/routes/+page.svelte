<script>
    import ThemeSelector from '$lib/ThemeSelector.svelte';


</script>
<body>
<h1>
    Svelte Theme Selector!
</h1>
<h2>
    Try it now!
</h2>
<ThemeSelector/>
</body>
<style>
    body{
        background-color: var(--color-100); 
    }
    h1{ 
        color: var(--text-100);
    }
    h2{
        color: var(--text-200);
    }
</style>
<script>
    import ThemeSelector from '$lib/ThemeSelector.svelte';


</script>
<body>
<main>
    <section class="outer-panel">
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
    </section>
    <section class="outer-panel">
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
        <section>
            <h2>Lorem</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, placeat laborum fugiat voluptate repellat quaerat, assumenda deserunt soluta mollitia quidem necessitatibus officia facere, doloremque porro autem tempora? Molestiae, modi inventore!</p>
        </section>
    </section>
</main>
<ThemeSelector/>
</body>
<style>
    *{
        margin: 0;
        padding: 0;
    }
    main{
        background-color: var(--color-100);
        color: var(--text-100);
    }
    main h2{
        color: var(--text-300);
    }
    
    .outer-panel{
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
    }
    section{
        padding: 0.2rem;
        background-color: var(--color-300);
        margin: 1rem;
        border-radius: 0.4rem;
    }
    section section{
        padding: 1rem;
        background-color: var(--color-600);
    }

    body{
        background-color: var(--color-100); 
    }
    h2{
        color: var(--text-200);
    }
</style>
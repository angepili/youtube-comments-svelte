<script>
    import {
        createEventDispatcher
    } from 'svelte';
    import Logo from './logo.svg';
    import IconSearch from './iconsearch.svg';

    const dispatch = createEventDispatcher();

    export let video = '';
</script>


    <div class="container">
        <div class="column is-6 is-offset-3 has-text-centered">
            <h1 class="title">
                <Logo />
                Youtube in Svelte.js
            </h1>
            <p class="content">Sistema di ricerca tramite API, con restituzione risultati e dettaglio video con embed + commenti + video correlati.</p>
            <div class="box">
                <div class="field is-grouped">
                    <p class="control is-expanded">
                        <input 
                            class="input" 
                            type="text" 
                            placeholder="Inserisci una parola chiave"
                            bind:value={video}
                        >
                    </p>
                    <p class="control">
                        <button
                            on:click={()=>dispatch('setVideo',video)}
                            class="button is-danger">
                            <IconSearch />
                        </button>
                    </p>
                </div>
            </div>
        </div>
    </div>


<style>
    .title :global(svg){
        width: 250px;
        display: block;
        margin: 0 auto;
    }
    .button :global(svg) {
        width: 24px;
        fill: #fff;
    }
</style>
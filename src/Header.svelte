<script>
  import {
    createEventDispatcher
  } from 'svelte';
  import Logo from './logo.svg';
  import IconSearch from './iconsearch.svg';

  const dispatch = createEventDispatcher();

  export let video = '';
</script>


  <nav class="navbar is-fixed-top">
    <div class="container">
      <div class="navbar-brand">
        <div id="logo">
          <a href="/"><Logo /></a>
        </div>
        <span class="navbar-burger burger" data-target="navbarMenu">
          <span></span>
          <span></span>
          <span></span>
        </span>
      </div>
      <div id="navbarMenu" class="navbar-menu">
        <div class="navbar-end">
          <form on:submit|preventDefault={()=>dispatch('setVideo',video)}>
            <div class="field has-addons has-addons-fullwidth">
              <div class="control">
                <input class="input" type="text" placeholder="Cerca" bind:value={video}>
              </div>
              <div class="control">
                <button class="button is-light" on:click={()=>dispatch('setVideo',video)} >
                  <IconSearch />
                </button>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </nav>


<style>
  #logo :global(svg) {
    width: 120px;
  }
  .button :global(svg) {
    width: 24px;
    fill: #999;
  }
  .button {
    border: 1px solid #ccc !important;
  }
  .navbar {
    padding: 15px 0 5px;
    box-shadow: 0 4px 10px rgba(0,0,0,.1);
  }
</style>
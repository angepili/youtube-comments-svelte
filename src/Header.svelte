<script>
  import {createEventDispatcher} from 'svelte';
  import Logo from './logo.svg';
  import IconSearch from './iconsearch.svg';

  const dispatch = createEventDispatcher();

  export let video = '';


</script>
<nav class="navbar is-fixed-top" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io">
        <!-- <Logo /> -->
      </a>
      <a href="#header" role="button" class="navbar-burger" aria-label="menu" aria-expanded="false">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
      
    </div>
  
        <div class="column">
          <div class="field has-addons has-addons-right">
              <p class="control">
                <input class="input" type="text" placeholder="Cerca" bind:value={video} >
              </p>
              <p class="control">
                <button class="button is-light" on:click={()=>dispatch('setVideo',video)} >
                  <IconSearch />
                </button>
              </p>
            </div>
        </div>
    

  </nav>

  <style>
      .navbar-item :global(svg) {
          width: 120px;
      }
      .button :global(svg) {
          width: 24px;
          fill: #999;
      }
      .button {
          border: 1px solid #ccc!important;
      }
  </style>
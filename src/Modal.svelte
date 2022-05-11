<script lang="ts">
  // Common event modifiers:
  // once - makes sure the event can only fire once (removes handler)
  // preventDefault - prevent the default action (run e.preventDefault())
  // self - only fires the event if the clicked element is the target

  export let message = 'Default message';
  export let isPromo = false;
  export let showModal = false;
</script>

{#if showModal}
  <div on:click|self class="backdrop" class:promo={isPromo}>
    <div class="modal">
      <p>{message}</p>
    </div>
  </div>
{/if}

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }

  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
  }

  .promo .modal {
    background: crimson;
    color: white;
  }
</style>

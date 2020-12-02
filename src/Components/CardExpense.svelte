<script>
  import {createEventDispatcher} from 'svelte'
  // export props
  export let id;
  export let name;
  export let amount;

  const dispatch = createEventDispatcher(); // instanciate

  // Custom event
  const sendDelete = () => {
    dispatch('delete-element', {id: id})
  }
</script>

<div class="card my-3">
  <div class="card-body">
      <h3>{name}</h3>
      <p>{amount}</p>
      <i class="trash" on:click={sendDelete}>
          <!-- In public folder -->
          <img src="ressources/trash-solid.svg" alt="">
      </i>
  </div>
</div>

<style>
  .card {
      position: relative;
  }
  .card h3 {
      font-size: 35px;
  }
  .card p {
      font-weight: 300;
      font-size: 25px;
  }
  i {
      cursor: pointer;
  }
  i img {
      width: 30px;
  }
  .trash {
      position: absolute;
      top: 10px;
      right: 20px;
  }
</style>
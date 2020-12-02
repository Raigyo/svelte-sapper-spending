<script>

  import {createEventDispatcher} from 'svelte'
  const dispatch = createEventDispatcher(); // instanciate

  let objNvDep = {
    name: '',
    amount: ''
  }

  const newExpense = () => {
    // console.log(objNvDep);
    // Custom event
    dispatch('nv-expense', {name:objNvDep.name, amount:objNvDep.amount});
    objNvDep.name = '';
    objNvDep.amount = '';
  }
</script>

<form class="mt-5" on:submit|preventDefault={newExpense}>
  <!-- label -->
  <div class="form-group">
    <label for="" class="lead font-weight bold">
      Expense name
    </label>
    <input
      bind:value={objNvDep.name}
      type="text"
      id="expense"
      placeholder="Insert a new expense"
      class="form-control"
    >
  </div>
  <div class="form-group">
    <label for="" class="lead font-weight bold">
      Expense value
    </label>
    <input
      bind:value={objNvDep.amount}
      type="number"
      id="expense"
      placeholder="Insert a value"
      class="form-control"
    >
  </div>
  <button type="submit" class="btn btn-primary">Add expense</button>
</form>
<script>
  import FormExpense from './FormExpense.svelte'
  import CardExpense from './CardExpense.svelte'
  import {v4 as uuidv4} from 'uuid'

  let arrayCards = [
    {
        id: uuidv4(),
        name: 'Shoping',
        amount: 300
    },
    {
        id: uuidv4(),
        name: 'Hobbies',
        amount: 150
    },
    {
        id: uuidv4(),
        name: 'Reading',
        amount: 100
    }
  ]
  // Total
  // Callback acc = 0
  $: total = arrayCards.reduce((acc, curr) => {
       return acc += curr.amount;
  }, 0)

  const addExpense = (e) => {
    let nvObj = {id:uuidv4(), name:e.detail.name, amount:e.detail.amount};
    // we need to assign in a new array to rerender (so no push)
    arrayCards = [...arrayCards, nvObj];
  }

  const deleteCard = (e) => {
    // filter: new array according conditions: all excepted the item id deleted
    arrayCards = arrayCards.filter(item => item.id !== e.detail.id)
  }

</script>

<div class="container">
  <FormExpense on:nv-expense={addExpense}/>
<h2 class="my-4">Total expenses: {total}</h2>
  {#each arrayCards as spending (spending.id)}
  <CardExpense
    on:delete-element={deleteCard}
    id={spending.id}
    name={spending.name}
    amount={spending.amount}
  />
  {/each}
</div>
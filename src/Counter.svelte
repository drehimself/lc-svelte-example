<script>
  import { onMount } from "svelte";

  export let title = "My default title";
  let count = 0;
  let myText = "";
  const todos = [
    {
      id: 1,
      title: "Finish Svelte Screencast",
      isComplete: false,
    },
    {
      id: 2,
      title: "Go shopping",
      isComplete: false,
    },
    {
      id: 3,
      title: "Take over world",
      isComplete: false,
    },
  ];

  $: doubled = count * 2;

  $: {
    console.log(`multiple statements can be combined`);
    console.log(`the current count is ${count}`);
  }

  onMount(() => {
    console.log("Counter mounted");
  });

  function decrement() {
    count--;
  }

  function increment() {
    count++;
  }
</script>

<div>
  <h2>{title}</h2>
  <div>
    <div>Count is {count} Doubled is {doubled}</div>
    {#if count > 10}
      Count is high
    {:else if count > 5}
      Count is in between
    {:else}
      Count is low
    {/if}
    <div>
      <button on:click={() => count--}>Decrement</button>
      <button on:click={increment}>Increment</button>
    </div>
  </div>
  <div>
    <form action="#">
      <input type="text" bind:value={myText} />
      <div>{myText}</div>
    </form>
  </div>
  <div>
    <h1>Each</h1>
    <div class="hello">This is global</div>
    <ul>
      {#each todos as { id, title }, index (id)}
        <li>{index} {id} {title}</li>
      {/each}
    </ul>
  </div>
</div>

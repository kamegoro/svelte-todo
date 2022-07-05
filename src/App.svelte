<script lang="ts">
  let value: string = '';
  let items: { value: string; id: number }[] = [];
  function addItem(): void {
    const item: { value: string; id: number } = {
      value,
      id: Date.now(),
    };
    items = [...items, item];
  }

  function delItem(id: number): void {
    items = items.filter(v => v.id !== id);
  }
</script>

<main>
  <div>
    <input bind:value type="text" />
    <button on:click={() => addItem()}>送信</button>
  </div>
  <ul>
    {#each items as item}
      <li>
        <p>{item.value}</p>
        <button on:click={() => delItem(item.id)}>削除</button>
      </li>
    {/each}
  </ul>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

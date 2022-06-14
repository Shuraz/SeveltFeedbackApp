<script>
  let firstName = "Suraj";
  let lastName = "Pokhrel";
  let color = "pink";
  let showText = false;
  $: name = firstName + " " + lastName;
  let users = [
    {
      id: "1",
      name: "John1",
    },
    {
      id: "2",
      name: "John2",
    },
    {
      id: "3",
      name: "John3",
    },
  ];

  const toggle = () => {
    color = color === "pink" ? "gold" : "pink";
    showText = !showText;
    users = [...users, { id: "4", name: "John4" }];
  };
</script>

<main>
  <h1 style="color:{color}">Hello {name}!</h1>
  {#if showText}
    <p>
      Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
      how to build Svelte apps.
    </p>
  {:else}
    <p>No Text</p>
  {/if}
  <button on:click={() => (color = "gold")}>Click1</button>
  <button on:click={toggle}>Click To Toggle</button>
  {#each users as user (user.id)}
    <h2>
      {user.id}:{user.name}
    </h2>
  {/each}
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

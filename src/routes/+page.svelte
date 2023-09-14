<script lang="ts">
  import type { EventHandler, ChangeEventHandler } from "svelte/elements";

let todoList: string[] = [];
let todo = "";

const submitHandler: EventHandler <SubmitEvent, HTMLFormElement> = () => {
  todoList=[...todoList, todo];
  todo = "";
}

const inputHandler: ChangeEventHandler<HTMLInputElement>  = (e) => {
  const {value} = e.target as HTMLInputElement;
  todo = value;
};


</script>

<main>
<h1>Make Todo List</h1>

<form on:submit|preventDefault={submitHandler}>
  <input type="text" placeholder="write to do item" on:change={inputHandler} bind:value={todo}/>
  <button type="submit">click</button>
</form>

<ul>
  {#each todoList as todoList}
  <li>{todoList}</li>
  {/each}
</ul>
</main>


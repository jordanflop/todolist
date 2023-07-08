<script>
    import { onMount } from 'svelte';
  
    let items = [];
    let input;
  
    function add() {
      let item = input.value;
      
      if (input.value != "") {
        items = [...items, item];
        input.value = "";
      }
      console.log(items);
    }
  
    function del(index) {
      console.log("deleted");
      items = items.filter((item, i) => i !== index);
    }
  
    function handleKeyDown(event) {
      
      if (event.key === 'Enter') {
        add();
      }
    }
  
    onMount(() => {
      console.log('mounted');
    });
  </script>
  
  <main>
    <div>
      <input type="text" placeholder="enter a todo item" id="input" bind:this={input} on:keydown={handleKeyDown}>
    </div>

  
    <ul id="ul">
      {#each items as item, index}
        <div class="item-div">
          <li class="item">{item}</li>
          <img src="https://cdn-icons-png.flaticon.com/512/1214/1214428.png" alt="delete" class="delete" on:click={() => del(index)}>
        </div>
      {/each}
    </ul>
  </main>
  
  <style>


  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&display=swap');


  main {
    background-color: #4834d4;
    width: 15vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 5px;
  }

  #ul {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    margin: 0%;
    padding: 0%;
  }
  
  .item-div {
    background-color: #686de0;
    width: 8vw;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    list-style-type: none;
    margin-top: 0.5vh;
    margin-bottom: 1.5vh;
    border-radius: 5px;
    font-family: Inter;
    font-weight: 700;
    font-size: 1vw;
  }
  
  .item {
    margin: 0.5vw;

  }



  #input {
    width: 10vw;
    height: 3vh;
    margin-bottom: 1vh;
    margin-top: 1vh;
    border-radius: 5px;
    border-style: none;
    text-align: center;
    font-family: Inter;
    font-weight: 700;

  }

  .delete {
    width: 1vw;
    height: 1vw;
    
    margin-right: 1vw;
    cursor: pointer;
  }


  </style>
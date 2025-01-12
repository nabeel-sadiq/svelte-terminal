<script>
  let commandsInput;
  let enteredCommand;
  let history;
  //focusing when window loads
  window.addEventListener("load", () => {
    commandsInput.focus();
  });

  function reply(answer) {
    let commandP = document.createElement("h3");
    commandP.innerHTML = `C:&bsol;Users&bsol;Nabeel&gt;&nbsp;${enteredCommand}`;
    history.appendChild(commandP);

    let p = document.createElement("p");
    p.innerHTML = answer;
    history.appendChild(p);

    let br = document.createElement("br");
    history.appendChild(br);
  }

  function terminalCommands() {
    switch (enteredCommand) {
      case "name":
        reply("Ch. M. Nabeel Sadiq");
        break;
      case "country":
        reply("Pakistan 🇵🇰");
        break;
      case "city":
        reply("Islamabad");
        break;
      case "cls":
      case "clear":
        history.innerHTML = ""
        break;
      default:
        reply("Not a valid command. Available commands are name, city, country and cls/clear.")
        break;
    }
  }

  function onEnter(event) {
    if (event.key === "Enter") {
      terminalCommands();
      enteredCommand = "";
    }
  }
</script>

<div class="pt-8 pl-8 text-gray-400 md:text-2xl text-lg">
  <p>Svelte [Version ^5.15.0]</p>
  <p>(c) Svelte Corporation. All rights reserved.</p>
</div>
<div class="text-white p-8 sm:text-xl text-sm flex flex-col">
  <div bind:this={history} class="history"></div>

  <span class="flex">
    <p>C:&bsol;Users&bsol;Nabeel&gt;&nbsp;</p>
    <input
      onkeydown={onEnter}
      bind:value={enteredCommand}
      class="bg-black focus:border-none focus:outline-none"
      bind:this={commandsInput}
      type="text"
    />
  </span>
</div>

<style>
  :global(body) {
    background-color: black;
  }
</style>

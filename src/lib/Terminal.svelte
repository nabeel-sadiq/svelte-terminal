<script>
  let commandsInput;
  let enteredCommand;
  let history;
  // focusing when window loads
  window.addEventListener("load", () => {
    commandsInput.focus();
    if (commandsInput) {
      commandsInput.setAttribute("placeholder", "Ctrl + K");
      setTimeout(() => {
        commandsInput.removeAttribute("placeholder");
      }, 2000);
    }
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
    const commands = [
      { command: "youtube", description: "Opens Youtube" },
      { command: "insta", description: "Opens Instagram" },
      { command: "chat", description: "Opens ChatGPT" },
      { command: "fbise", description: "Opens FBISE site" },
      { command: "local", description: "Opens local development server" },
      { command: "github", description: "Opens GitHub" },
      { command: "name", description: "Displays the name" },
      { command: "country", description: "Displays the country" },
      { command: "city", description: "Displays the city" },
      { command: "cls", description: "Clears the screen" },
      { command: "clear", description: "Clears the screen" },
      { command: "google", description: "Opens Google" },
      { command: "twitter", description: "Opens Twitter" },
      { command: "docs", description: "Opens documentation" },
      { command: "reddit", description: "Opens Reddit" },
    ];

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
      case "youtube":
        window.open("https://youtube.com/", "_blank");
        break;
      case "insta":
        window.open("https://instagram.com/", "_blank");
        break;
      case "chat":
        window.open("https://chatgpt.com/", "_blank");
        break;
      case "fbise":
        window.open("https://fbise.vercel.app/", "_blank");
        break;
      case "local":
        window.open("http://localhost:5173/", "_blank");
        break;
      case "github":
        window.open("https://github.com/", "_blank");
        break;
      case "google":
        window.open("https://google.com/", "_blank");
        break;
      case "twitter":
        window.open("https://twitter.com/", "_blank");
        break;
      case "docs":
        window.open("https://developer.mozilla.org/en-US/docs/Web", "_blank");
        break;
      case "reddit":
        window.open("https://reddit.com/", "_blank");
        break;
      case "help":
        let helpText = "Available commands are:<br>";
        commands.forEach((cmd) => {
          helpText += `<span style="margin-left: 20px;">${cmd.command} - ${cmd.description}</span><br>`;
        });
        reply(helpText);
        break;
      case "cls":
      case "clear":
        history.innerHTML = "";
        break;
      default:
        reply("Not a valid command. Type 'help' for more information.");
        break;
    }
  }

  function onEnter(event) {
    if (event.key === "Enter") {
      terminalCommands();
      enteredCommand = "";
    }
  }

  // shortcut key functionality for focusing input on '/'
  window.addEventListener("keydown", (event) => {
    if ((event.metaKey || event.ctrlKey) && event.key === "k") {
      event.preventDefault();
      commandsInput.focus();
    }
  });
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

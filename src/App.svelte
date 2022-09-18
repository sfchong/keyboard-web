<script lang="ts">
  import Description from "./Description.svelte";
  import { onMount } from "svelte";
  import Footer from "./Footer.svelte";

  // prettier-ignore
  const base = [
        "Tab", "Q", "W", "F", "P", "G", "J", "L", "U", "Y", "", "", 
        "Ctrl","A", "R", "S", "T", "D", "H", "N", "E", "I", "O", "",
        "Shift", "Z", "X", "C", "V", "B", "K", "M", ",", ".", "/", "Shift",
        "Cmd", "Space", "Esc", "Enter", "Back Space", "OSM Shift"
    ]

  // prettier-ignore
  const nav = [
        "", "Cmd+`", "Alt+Tab", "", "", "", "Tab", "Page Down", "Page Up", "Home", "Caps Lock", "", 
        "","Shift", "Ctrl", "Option", "Cmd", "", "Left", "Down", "Up", "Right", "", "",
        "", "Undo", "Cut", "Copy", "Paste", "", "", "Ins", "Delete", "End", "", "",
        "", "Release", "", "", "", ""
    ]

  // prettier-ignore
  const number = [
        "", "", "", "", "", "", "", "7", "8", "9", "", "", 
        "","Shift", "Ctrl", "Option", "Cmd", "", "", "4", "5", "6", "", "",
        "", "", "", "", "", "", "0", "1", "2", "3", "", "",
        "", "", "Release", "", "", ""
    ]

  // prettier-ignore
  const symbol = [
        "", "!", "@", "#", "$", "[", "]", "&", "*", "|", "\\", "", 
        "Ctrl","~", "?", ":", ";", "(", ")", "=", "'", "\"", "/", "",
        "Shift", "_", "`", "<", ">", "{", "}", "-", "+", "%", "^", "",
        "", "", "", "", "Release", ""
    ]

  // prettier-ignore
  const system = [
        "", "F1", "F2", "F3", "F4", "F5", "F6", "F7", "F8", "F9", "F10", "Volume Up", 
        "","Shift", "Ctrl", "Option", "Cmd", "", "", "Cmd", "Option", "Ctrl", "Shift", "Volume Down",
        "", "", "", "", "", "", "F11", "F12", "", "", "", "Mute",
        "", "", "", "Release", "", ""
    ]

  enum layer {
    base,
    nav,
    number,
    symbol,
    system,
  }
  const keymap = [base, nav, number, symbol, system];

  let currentKeys: string[] = [];
  let currentLayer = 0;

  onMount(() => {
    currentKeys = base;
  });

  function handleClick(layerNo: number) {
    // reset layer
    if (currentLayer === layerNo) {
      currentKeys = base;
      currentLayer = 0;
      return;
    }

    currentKeys = keymap[layerNo] ?? base;
    currentLayer = layerNo;
  }
</script>

<main>
  <div class="container-keyboard-wrapper">
    <div class="container-keyboard">
      <div class="key" style="left: 10px; top: 30px;">{currentKeys[0]}</div>
      <div class="key" style="left: 80px; top: 30px">{currentKeys[1]}</div>
      <div class="key" style="left: 150px; top: 20px;">{currentKeys[2]}</div>
      <div class="key" style="left: 220px;">{currentKeys[3]}</div>
      <div class="key" style="left: 290px; top: 20px">{currentKeys[4]}</div>
      <div class="key" style="left: 360px; top: 30px">{currentKeys[5]}</div>

      <div class="key" style="right: 360px; top: 30px;">{currentKeys[6]}</div>
      <div class="key" style="right: 290px; top: 20px;">{currentKeys[7]}</div>
      <div class="key" style="right: 220px;">{currentKeys[8]}</div>
      <div class="key" style="right: 150px; top: 20px;">{currentKeys[9]}</div>
      <div class="key" style="right: 80px; top: 30px;">{currentKeys[10]}</div>
      <div class="key" style="right: 10px; top: 30px;">{currentKeys[11]}</div>

      <div class="key" style="left: 10px; top: 100px;">{currentKeys[12]}</div>
      <div class="key" style="left: 80px; top: 100px;">
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">Shift</div>
          {/if}
          {currentKeys[13]}
        </div>
      </div>
      <div class="key" style="left: 150px; top: 90px;">
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">Ctrl</div>
          {/if}
          {currentKeys[14]}
        </div>
      </div>
      <div class="key" style="left: 220px; top: 80px;">
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">Option</div>
          {/if}
          {currentKeys[15]}
        </div>
      </div>
      <div class="key" style="left: 290px; top: 90px;">
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">Cmd</div>
          {/if}
          {currentKeys[16]}
        </div>
      </div>
      <div class="key" style="left: 360px; top: 100px;">
        {currentKeys[17]}
      </div>

      <div class="key" style="right: 360px; top: 100px;">
        {currentKeys[18]}
      </div>
      <div class="key" style="right: 290px; top: 90px;">
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">Cmd</div>
          {/if}
          {currentKeys[19]}
        </div>
      </div>
      <div class="key" style="right: 220px; top: 80px;">
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">Option</div>
          {/if}
          {currentKeys[20]}
        </div>
      </div>
      <div class="key" style="right: 150px; top: 90px;">
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">Ctrl</div>
          {/if}
          {currentKeys[21]}
        </div>
      </div>
      <div class="key" style="right: 80px; top: 100px;">
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">Shift</div>
          {/if}
          {currentKeys[22]}
        </div>
      </div>
      <div class="key" style="right: 10px; top: 100px;">
        {currentKeys[23]}
      </div>

      <div class="key" style="left: 10px; top: 170px;">{currentKeys[24]}</div>
      <div class="key" style="left: 80px; top: 170px;">{currentKeys[25]}</div>
      <div class="key" style="left: 150px; top: 160px;">
        {currentKeys[26]}
      </div>
      <div class="key" style="left: 220px; top: 150px;">
        {currentKeys[27]}
      </div>
      <div class="key" style="left: 290px; top: 160px;">
        {currentKeys[28]}
      </div>
      <div class="key" style="left: 360px; top: 170px;">
        {currentKeys[29]}
      </div>

      <div class="key" style="right: 360px; top: 170px;">
        {currentKeys[30]}
      </div>
      <div class="key" style="right: 290px; top: 160px;">
        {currentKeys[31]}
      </div>
      <div class="key" style="right: 220px; top: 150px;">
        {currentKeys[32]}
      </div>
      <div class="key" style="right: 150px; top: 160px;">
        {currentKeys[33]}
      </div>
      <div class="key" style="right: 80px; top: 170px;">
        {currentKeys[34]}
      </div>
      <div class="key" style="right: 10px; top: 170px;">
        {currentKeys[35]}
      </div>

      <!-- left thumb cluster -->
      <div class="key" style="left: 250px; top: 230px;">
        {currentKeys[36]}
      </div>
      <button
        class="key"
        style="left: 330px; top: 240px; transform: rotate(20deg);"
        on:click={() => handleClick(layer.nav)}
      >
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">LT1</div>
          {/if}
          {currentKeys[37]}
        </div>
      </button>
      <button
        class="key key-large"
        style="left: 415px; top: 240px; transform: rotate(40deg);"
        on:click={() => handleClick(layer.number)}
      >
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">LT2</div>
          {/if}
          {currentKeys[38]}
        </div>
      </button>

      <!-- right thumb cluster -->
      <button
        class="key key-large"
        style="right: 415px; top: 240px; transform: rotate(-40deg);"
        on:click={() => handleClick(layer.system)}
      >
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">LT4</div>
          {/if}
          {currentKeys[39]}
        </div>
      </button>
      <button
        class="key"
        style="right: 330px; top: 240px; transform: rotate(-20deg);"
        on:click={() => handleClick(layer.symbol)}
      >
        <div>
          {#if currentLayer === layer.base}
            <div class="key-secondary">LT3</div>
          {/if}
          {currentKeys[40]}
        </div>
      </button>
      <div class="key" style="right: 250px; top: 230px;">
        {currentKeys[41]}
      </div>
    </div>
  </div>

  <Description />
</main>

<Footer />

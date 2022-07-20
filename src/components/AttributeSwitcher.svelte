<script>
  const attributes = ["Full Stack Developer", "React.JS Developer", ".NET Developer"];

  let currentAttribute = attributes[0];
  let currentIndex = 0;

  let displayedWord = "";

  function decreaseLetters() {
    if (displayedWord.length === 0) {
      setTimeout(() => {
        if (currentIndex + 1 > attributes.length - 1) {
          currentIndex = 0;
        } else {
          currentIndex += 1;
        }

        currentAttribute = attributes[currentIndex];
      }, 1000);
      return;
    }

    displayedWord = displayedWord.substring(0, displayedWord.length - 1) ?? "";
    setTimeout(decreaseLetters, 50);
  }

  function increaseLetters(letters = "") {
    if (letters.length === 0) {
      setTimeout(decreaseLetters, 1500);
      return;
    }

    displayedWord += letters[0];
    setTimeout(() => increaseLetters(letters.substring(1, letters.length)), 75);
  }

  $: {
    increaseLetters(currentAttribute + "...");
  }
</script>

<p>
  {#if displayedWord.length !== 0}
    {displayedWord}
  {:else}
    &nbsp;
  {/if}
</p>

<style>
  P {
    font-size: 1.2rem;
  }
</style>

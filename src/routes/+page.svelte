<script>
  import { browser }  from "$app/environment";

  let scratch = "";
  let timer;

  if (browser) {
    scratch = localStorage.getItem('thunks') || "";
  }

  const debounce = () => {
    clearTimeout(timer);
    timer = setTimeout(() => {
      localStorage.setItem("thunks", scratch);
      console.log(scratch);
    }, 750);

  }
</script>

<h1>Thunks.io</h1>
<div contenteditable="true" bind:innerHTML={scratch} on:keyup={() => debounce() }></div>

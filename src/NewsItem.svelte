<script>
  export let news;
  let hidden = true;
  
  function open(){
    hidden = !hidden
  }
  
</script>

{#if news.length > 0}
<article class="item" class:is-open={!hidden}>
  <div class="news-wrapper">
    <header>
      <h2>{news[0].title}</h2>
      <p>แหล่งข่าว: {news[0].source.name}</p>
      {#if news[0].author}<p>โดย: {news[0].author}</p>{/if}
    </header>
    <div class="news-content" class:hidden>
      <img src="{news[0].urlToImage}" alt="{news[0].title}" /> 
      <p>{news[0].description}</p>
    </div>
  </div>
  <span class="news-plus-wrapper" on:click={open}>
    <span class="news-plus"></span>
  </span>
</article>
<svelte:self news="{news.splice(1)}"/>
{/if}

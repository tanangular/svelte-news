<script>
  import NewsItem from "./NewsItem.svelte";
  let newsAPI = 'https://newsapi.org/v2/top-headlines?country=th&category=business&apiKey=36de87b41bc74690bea3dd3f58d81760';
  const fetchNews = async () => {
    const response = await fetch(newsAPI);
    const news = await response.json();
    return news.articles;
   
	}
</script>

<main>
{#await fetchNews() then news }
  <NewsItem {news}/>
{/await}
</main>

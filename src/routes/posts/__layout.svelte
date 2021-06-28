<script context="module">
  export async function load() {
    const posts = import.meta.globEager('../../posts/*.md');
    const postsList = Object.values(posts);
    const postsMeta = postsList.map(post => {
      return post.metadata
    })
    return {
      props: {
        posts: postsMeta
      }
    }
  }
</script>

<script>
  export let posts;
</script>
<div class="wrapper">
  <article><slot/></article>
  <aside>
  <h2>Blog Posts</h2>
  <ul>
    {#each posts as post}
      <li><a href={post.slug}>{post.title}</a></li>
    {/each}
  </ul></aside>
</div>
<style>
  @media(min-width: 768px) {
    .wrapper {
      display: grid;
      grid-template-columns:  800px 1fr;
      gap: 2rem;
    }
    h2 {
      margin-top: 0;
    }
    aside {
      padding-top: 1em
    }
  }
</style>


<script context="module">
  export async function load({page}) {
  try {
      const Post = await import(`../../posts/${page.params.slug}.md`);
      return {
        props: {
          Post: Post.default
        }
      }
    } catch(err) {
      return {
        status: 404,
        error: 'Page not found'
      }
    }
  }
</script>
<script>
  export let Post

</script>
<svelte:component this={Post}/>
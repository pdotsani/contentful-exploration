<script lang="ts">
  import { 
    PUBLIC_CONTENTFUL_SPACE_ID,
    PUBLIC_DEVELOPMENT_ENVIRONMENT,
    PUBLIC_CONTENTFUL_ACCESS_TOKEN,
    PUBLIC_TEST_ENTRY_ID 
  } from '$env/static/public';

  let post: any;
  
  fetch(`https://cdn.contentful.com/spaces/${PUBLIC_CONTENTFUL_SPACE_ID}/environments/${PUBLIC_DEVELOPMENT_ENVIRONMENT}/entries/${PUBLIC_TEST_ENTRY_ID}?access_token=${PUBLIC_CONTENTFUL_ACCESS_TOKEN}`)
    .then(res => res.json())
    .then(data => {
      console.log(data);
      post = data;
    })
    .catch(err => console.log(err));

  console.log("post inside", post);
</script>

{#if post.fields}
  {#each post.fields.blogBody.content as content}
    {#each content.content as c}
      <div>{c[0].value}</div>
    {/each}
  {/each}
{/if}

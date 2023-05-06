<script lang="ts">
  import { onMount } from "svelte";

  interface Repo {
    name: string;
    url: string;
    homepage: string;
  }

  let repos: Repo[] = [];

  onMount(async () => {
    repos = await fetch("/gh-repos.json").then((res) => res.json());
  });
</script>

<main>
  <h6>I am not a web dev</h6>

  {#each repos as repo}
    <div class="card">
      <a href={repo.url} class="button">{repo.name}</a>
      <a href={repo.homepage} class="button">Homepage</a>
    </div>
  {/each}
</main>

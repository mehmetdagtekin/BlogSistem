<script lang="ts" context="module">
  import Image from '$lib/components/prose/img.svelte'
  import table from '$lib/components/prose/table.svelte'
  export { Image as img, table }
</script>

<script lang="ts">
  import Head from '$lib/components/head.svelte'
  import Post from '$lib/components/layouts/_post.svelte'

  export let path = undefined
  export let created = undefined
  export let updated = undefined
  export let published = undefined
  export let tags = undefined
  export let flags = undefined

  export let photo = undefined
  export let alt = undefined
</script>

<Head post={{ layout: 'photo', path, created, updated, published, tags, flags, photo, alt }} />

<Post post={{ layout: 'photo', path, created, updated, published, tags, flags, photo, alt }}>
  <figure slot="top" class="flex-col gap-2 mx-4 md:mx-0 w-auto">
    <Image src={photo} alt={alt ?? photo} class="rounded-box w-full shadow-xl" loading="eager" decoding="auto" />
    {#if alt}
      <figcaption>{@html alt}</figcaption>
    {/if}
  </figure>
  <main slot="content" itemprop="articleBody" class="urara-prose prose p-name p-content">
    <slot />
  </main>
</Post>

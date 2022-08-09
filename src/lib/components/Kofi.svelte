<script lang="ts">
    import LibLoader from './LibLoader.svelte'
  
    export let name: string
    export let label = 'Buy me Coffee'
  
    const loadKofiWidget = () => {
      window.kofiWidgetOverlay?.draw(
        name,
        {
          type: 'floating-chat',
          'floating-chat.donateButton.text': label,
          'floating-chat.donateButton.background-color': 'orange',
          'floating-chat.donateButton.text-color': 'black'
        },
        'kofiContainer'
      )
    }
  </script>
  
  {#if name}
    <div id="kofiContainer" class="web-only">{label}</div>
  
    <LibLoader
      on:load={loadKofiWidget}
      src="https://storage.ko-fi.com/cdn/scripts/overlay-widget.js"
      libraryDetectionObject="kofiWidgetOverlay"
    />
  {/if}
  
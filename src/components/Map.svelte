<script>
  import { onMount, afterUpdate } from 'svelte';
  onMount(async () => {
    let Map = (await import('ol/Map')).default,
      View = (await import('ol/View')).default,
      TileLayer = (await import('ol/layer/Tile')).default,
      XYZ = (await import('ol/source/XYZ')).default;
    new Map({
      target: 'map',
      layers: [
        new TileLayer({
          source: new XYZ({
            url: 'https://{a-c}.tile.openstreetmap.org/{z}/{x}/{y}.png'
          })
        })
      ],
      view: new View({
        center: [0, 0],
        zoom: 2
      })
    });
  });
  export let componentName = 'Map'
</script>

<svelte:head>
  <link rel="stylesheet" href="https://openlayers.org/en/latest/css/ol.css" type="text/css">
</svelte:head>

<div id="map"/>

<style>
  :global(main) {
    margin: unset !important;
    max-width: unset !important;
    padding: unset !important;
    height: 100%;
  }
  #map {
    position: fixed;
    height: 100%;
    width: 100%;
  }
</style>

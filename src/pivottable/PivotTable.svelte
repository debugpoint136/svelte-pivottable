<script>
  import TableRenderer from './TableRenderer.svelte';
/**
render() {
    const Renderer = this.props.renderers[
      this.props.rendererName in this.props.renderers
        ? this.props.rendererName
        : Object.keys(this.props.renderers)[0]
    ];
    return <Renderer {...this.props} />;
  }
  
 **/

</script>

<div class="pvtOutput">
  <!-- will call TableRenderer from here -->
  <TableRenderer/>
</div>
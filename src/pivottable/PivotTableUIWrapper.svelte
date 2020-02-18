<!-- <PivotTableUI
  renderers={Object.assign({}, TableRenderers)}
  {...this.state.pivotState}
  onChange={s => this.handleFacetStateChange(s)}
  onClick={this.handleCellClick}
  unusedOrientationCutoff={Infinity}/> -->

<script>
  import PivotTableUI from './PivotTableUI.svelte';
</script>
  <div class="test">
    <PivotTableUI />
  </div>
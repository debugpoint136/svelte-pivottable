<!-- <PivotTable
          {...update(this.props, {
            data: {$set: this.materializedInput},
          })}
        /> -->
<script>
  import PivotTable from './PivotTable.svelte';
</script>

<div class="">
  <PivotTable/>
   <!-- <table className="pvtUi">
        <tbody onClick={() => this.setState({openDropdown: false})}>
          <tr>
            {rendererCell}
            {aggregatorCell}
            {colAttrsCell}
          </tr>
          <tr>
            {unusedAttrsCell}
            {rowAttrsCell}
            {outputCell}
          </tr>
        </tbody>
      </table> -->
</div>
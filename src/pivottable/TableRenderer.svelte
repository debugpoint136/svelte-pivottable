<script>
  import TESTDATA from "../json/table_test.data.json";
  import { PivotData } from "./Utilities";

  const pivotData = new PivotData(TESTDATA);
  let colAttrs = pivotData.props.cols;
  let rowAttrs = pivotData.props.rows;
  let rowKeys = pivotData.getRowKeys();
  let colKeys = pivotData.getColKeys();
  import { spanSize } from "./helper";
</script>

<table class="pvtTable">
  <thead>
    {#each colAttrs as c, j}
      <tr key={`colAttr${j}`}>
        <th colSpan={rowAttrs.length} rowSpan={colAttrs.length} />
        <th class="pvtAxisLabel">{c}</th>
        {#each colKeys as colKey, i}
          {#if spanSize(colKeys, i, j) !== -1}
            <th
              class="pvtColLabel"
              key={`colKey${i}`}
              colSpan={spanSize(colKeys, i, j)}
              rowSpan={j === colAttrs.length - 1 && rowAttrs.length !== 0 ? 2 : 1}>
              {#if colAttrs.length > 1 && colAttrs.length - 1 === j}
                <div class="rotate text-xs">{colKey[j]}</div>
              {:else}{colKey[j]}{/if}
            </th>
          {/if}
        {/each}
      </tr>
    {/each}

    {#each rowAttrs as r, i}
      <th class="pvtAxisLabel" key={`rowAttr${i}`}>{r}</th>
    {/each}
  </thead>

  <tbody>
    {#each rowKeys as rowKey, i}
      <tr key={`rowKeyRow${i}`}>
        {#each rowKey as txt, j}
          {#if spanSize(rowKeys, i, j) !== -1}
            <th
              key={`rowKeyLabel${i}-${j}`}
              class="pvtRowLabel"
              rowSpan={spanSize(rowKeys, i, j)}
              colSpan={j === rowAttrs.length - 1 && colAttrs.length !== 0 ? 2 : 1}>
              {#if rowAttrs.length !== 1 && spanSize(rowKeys, i, j) > 3}
                <div className="rotate90">{txt}</div>
              {:else}{txt}{/if}
            </th>
          {/if}
        {/each}
      </tr>
      {#each colKeys as colKey, j}
        <td class={`pvtVal pvtValue`} key={`pvtVal${i}-${j}`} on:click={() => alert(pivotData.getAggregator(rowKey, colKey).value())}>
          {pivotData.getAggregator(rowKey, colKey).value()}
        </td>
      {/each}
    {/each}
  </tbody>
</table>

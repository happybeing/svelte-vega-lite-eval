<script>
import {onMount} from 'svelte';
import {default as embed}  from 'vega-embed';

import simpleChartSpec from './vl-specs/vega-simple-chart.js';
import lineMultipleSpec from './vl-specs/line-multiple.vl.json';
import scatterplotSpec from './vl-specs/scatterplot.vl.json';
import circleTimelineSpec from './vl-specs/circle_timeline.vl.json';
import treeSpec from './vl-specs/tree.vg.json';
import treemapSpec from './vl-specs/treemap.vg.json';
import choroplethSpec from './vl-specs/choropleth.vl.json';
import forceGraphSpec from './vl-specs/force.vg.json';

// For debugging
import {compile} from 'vega-lite';

onMount(() => {
  // For debugging
  console.log('Compiling...')
  const vgSpec = compile(lineMultipleSpec).spec
  console.dir(vgSpec);

   embed("#bar-chart", simpleChartSpec, { actions: false }).catch(error => console.log(error) );
   embed("#line-chart", vgSpec, { actions: false }).catch(error => console.log(error) );
   embed("#scatter-plot", scatterplotSpec, { actions: false }).catch(error => console.log(error) );
   embed("#time-series", circleTimelineSpec, { actions: false }).catch(error => console.log(error) );
   embed("#tree", treeSpec, { actions: false }).catch(error => console.log(error) );
   embed("#treemap", treemapSpec, { actions: false }).catch(error => console.log(error) );
   embed("#force-graph", forceGraphSpec, { actions: false }).catch(error => console.log(error) );
   embed("#geospacial", choroplethSpec, { actions: false }).catch(error => console.log(error) );
});

</script>

<style>
.example { width: 250px; height: 280px; }
</style>

<div>
<b>TODO: </b><input type="checkbox" /> generate Vega-Lite data for each visualisation from a single RDF dataset.<br/>
</div>
<div>
  <h2>Vega and Vega-Lite Charts</h2>
  <p>The following charts use Vega-Lite specifications except for the Tree, Tree Map and Force Graph which use Vega.</p>
  <div>
    <div style="float: left;">
      <h3>Bar Chart</h3>
      <div class='example' id='bar-chart'></div>
    </div>  
    <div style="float: left;">
      <h3>Line Chart</h3>
      <div class='example' id='line-chart'></div>
    </div>  
    <div style="float: left;">
      <h3>Scatter Plot</h3>
      <div class='example' id='scatter-plot'></div>
    </div>  
    <div style="float: left;">
      <h3>Tree</h3>
      <div class='example' id='tree'></div>
    </div>  
    <div style="float: left;">
      <h3>Tree Map</h3>
      <div class='example' id='treemap'></div>
    </div>  
    <div style="float: left;">
      <h3>Geospacial</h3>
      <div class='example' id='geospacial'></div>
    </div>  
    <div style="float: left;">
      <h2>Force Graph</h2>
      <div class='example' id='force-graph'></div>
    </div>
    <br/>
    <div style="float: left;">
      <h3>Time Series</h3>
      <div class='example' id='time-series'></div>
    </div>  
  </div>
</div>
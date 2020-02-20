<script>
import {onMount} from 'svelte';
import {default as embed}  from 'vega-embed';

import simpleChartSpec from './vl-specs/vega-simple-chart.js';
import lineMultipleSpec from './vl-specs/line-multiple.vl.json';
import scatterplotSpec from './vl-specs/scatterplot.vl.json';
import circleTimelineSpec from './vl-specs/circle_timeline.vl.json';
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
  //  embed("#tree", simpleChartSpec, { actions: false }).catch(error => console.log(error) );
   embed("#force-graph", forceGraphSpec, { actions: false }).catch(error => console.log(error) );
   embed("#geospacial", choroplethSpec, { actions: false }).catch(error => console.log(error) );
});

</script>
<div>
<h2>TODO</h2>
<input type="checkbox" /> generate Vega-Lite data for each visualisation from a single RDF dataset.<br/>
<input type="checkbox" /> create a test dataset and visualisation for each of the following:<br/>
<ul>
<input type="checkbox" checked/> bar chart<br/>
<input type="checkbox" checked/> line chart<br/>
<input type="checkbox" checked/> scatter plot<br/>
<input type="checkbox" checked/> time series<br/>
<input type="checkbox" /> tree<br/>
<input type="checkbox" checked/> geographical projection<br/>
<input type="checkbox" checked/> force graph<br/>
</ul>
</div>
<div>
  <h2>Vega-Lite Charts</h2>
  <div>
    <div style="float: left;">
      <h3>Bar Chart</h3>
      <div id='bar-chart'></div>
    </div>  
    <div style="float: left;">
      <h3>Line Chart</h3>
      <div id='line-chart'></div>
    </div>  
    <div style="float: left;">
      <h3>Scatter Plot</h3>
      <div id='scatter-plot'></div>
    </div>  
    <div style="float: left;">
      <h3>Time Series</h3>
      <div id='time-series'></div>
    </div>  
    <div style="float: left;">
      <h3>Tree</h3>
      <div id='tree'></div>
    </div>  
    <div style="float: left;">
      <h3>Geospacial</h3>
      <div id='geospacial'></div>
    </div>  
    <div style="float: left;">
      <h2>Force Graph</h2>
      <div id='force-graph'></div>
    </div>
  </div>
</div>
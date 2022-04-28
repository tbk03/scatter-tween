<script>
    import { LayerCake, Svg } from 'layercake';
	import { tweened } from "svelte/motion";
    import * as eases from 'svelte/easing';


	import AxisX from './AxisX.svelte';
	import AxisY from './AxisY.svelte';
	import ScatterSvg from './Scatter.svg.svelte';

    export let data;

    const tweenOptions = {
    duration: 300,
    easing: eases.cubicInOut
  };

  const dataTween = tweened(undefined, tweenOptions);

  $: data_now = dataTween.set(data);

</script>
<div class="chart-container">
    <LayerCake
    padding={{ right: 10, bottom: 20, left: 25, top:30 }}
        x='x'
        y='y'
        yDomain={[0, null]}
        data={data_now}>
        
        <Svg>
            <AxisX/>
            <AxisY/>
            <ScatterSvg/>
        </Svg>
        
    </LayerCake>
</div>

<style>
	.chart-container {
		width: 100%;
		height: 400px;
	}
</style>
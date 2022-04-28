<script>
	import { LayerCake, Svg } from 'layercake';

	import Line from './_components/Line.svelte';
	import Area from './_components/Area.svelte';
	import AxisX from './_components/AxisX.svelte';
	import AxisY from './_components/AxisY.svelte';
	import ScatterSvg from './_components/Scatter.svg.svelte';

	import points from './_data/points.csv';

	const xKey = 'myX';
	const yKey = 'myY';

	points.forEach(row => {
		row[yKey] = +row[yKey];
	});

	
	// for simple scatter chart
	let data1 = [	{x: 0, y: 0},
					{x: 5, y: 5},
					{x: 10, y: 10}
				];

	let data2 = [	{x: 0, y: 0},
					{x: 0, y: 5},
					{x: 0, y: 10}
				];
	
	$: data = data1;

	function handleButton1(){
		data = data1;
	}

	function handleButton2(){
		data = data2;
	}

</script>

<style>
	.chart-container {
		width: 100%;
		height: 400px;
	}
</style>

<div class="chart-container">
	<!-- <LayerCake
		padding={{ right: 10, bottom: 20, left: 25 }}
		x={xKey}
		y={yKey}
		yDomain={[0, null]}
		data={points}
	>
		<Svg>
			<AxisX/>
			<AxisY/>
			<Line/>
			<Area/>
		</Svg>

		<Svg>
			<ScatterSvg/>
		</Svg>
	</LayerCake> -->

	<button on:click={handleButton1}>Data one</button>
	<button on:click={handleButton2}>Data two</button>

	<LayerCake
	padding={{ right: 10, bottom: 20, left: 25, top:30 }}
		x='x'
		y='y'
		yDomain={[0, null]}
		data={data}>
		
		<Svg>
			<!-- <AxisX/>
			<AxisY/> -->
			<ScatterSvg/>
		</Svg>
		
	</LayerCake>
</div>

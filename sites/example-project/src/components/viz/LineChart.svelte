<script>
    import Chart from './Chart.svelte'
    import Line from './Line.svelte'

    export let data = undefined;
    export let x = undefined;
    export let y = undefined;
    export let series = undefined;
    export let xType = undefined;

    export let title = undefined;
    export let subtitle = undefined;
    export let legend = undefined;
    export let xAxisTitle = undefined;
    export let yAxisTitle = undefined;
    export let xGridlines = undefined;
    export let yGridlines = undefined;
    export let xAxisLabels = undefined;
    export let yAxisLabels = undefined;
    export let xBaseline = undefined;
    export let yBaseline = undefined;
    export let xTickMarks = undefined;
    export let yTickMarks = undefined;
    export let yMin = undefined;
    export let yMax = undefined;

    export let lineColor = undefined;
    export let lineType = undefined;
    export let lineOpacity = undefined;
    export let lineWidth = undefined;

    export let markers = undefined;
    export let markerShape = undefined;
    export let markerSize = undefined;

    export let handleMissing = undefined;

    export let sort = undefined;

    let chartType = "Line Chart";

</script>

<Chart
    {data}
    {x}
    {y}
    {series}
    {xType}
    {legend}
    {xAxisTitle}
    {yAxisTitle}
    {xGridlines}
    {yGridlines}
    {xAxisLabels}
    {yAxisLabels}
    {xBaseline}
    {yBaseline}
    {xTickMarks}
    {yTickMarks}
    {yMin}
    {yMax}
    {title}
    {subtitle}
    {chartType}
    {sort}
    >
    <Line
        {lineColor}
        {lineWidth}
        {lineOpacity}
        {lineType}
        {markers}
        {markerShape}
        {markerSize}
        {handleMissing}
    />
</Chart>
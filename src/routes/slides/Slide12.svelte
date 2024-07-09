<script>
    import Slide from '$lib/Slide.svelte';
    import {scaleLinear} from 'd3-scale';
    import {axisLeft} from 'd3-axis';
    import * as d3 from 'd3';

    import { tweened } from 'svelte/motion';


    let svg_width;
    let svg_height = 600;
    let margins = {top: 20, bottom: 20, left: 20, right: 20}

    $: chartWidth = svg_width - margins.left - margins.right;
    $: chartHeight = svg_height - margins.top - margins.bottom;

    $: yScale = scaleLinear().domain([0, 100]).range([0, chartHeight]);

    // $: console.log(yScale(100));

    // $: console.log(svg_width);

    $: chartCentre = svg_width / 2;
    // $: console.log("chart centre" + chartCentre)

    let yAxis;

    $: d3.select(yAxis).call(axisLeft(yScale));

    $: console.log(yScale(25))

    // $: console.log(yAxis);

    // let barHeight = tweened(0);

    // function updateBarHeight(e) {
    //     if(e.key === 'Right') {
    //         barHeight.set(6.9, { duration: 500 });
    //     }
    // }
    
</script>

<Slide bgColor="#8db3cf">

    <div class="content">
        <section>
            <div class="r-stack">
                <p class="sticky fragment fade-out">Oliver actually follows this structure quite closely.</p>
                <p class="sticky fragment fade-in">And it's repeated pretty consistently throughout the story.</p>
            </div>
            <div class="bar-chart" bind:clientWidth = { svg_width }>
                <svg width={svg_width} height={svg_height}>
                    <g transform={`translate(${margins.left}, ${margins.top})`}>
                        <rect x="185" y="0" width="{yScale(25)}" height="500" fill="#dbcdf0" ></rect>
                        <rect x="327" y="0" width="{yScale(25)}" height="500" fill="#faedcb" ></rect>
                        <rect x="469" y="0" width="{yScale(25)}" height="500" fill="#f7d9c4" ></rect>
                        <rect x="{chartHeight + 50}" y="0" width="{yScale(25)}" height="500" fill="#FFADAD" ></rect>
                    </g>
                    <!-- <g transform="translate({chartCentre - margins.left}, {margins.top})" bind:this={yAxis} /> -->
                </svg>
            </div>
        </section>

    </div>

</Slide>

<style>

    .content {
        margin: auto;
        padding: 50px;
    }
    
    #hero {
        width: 100%;
        height: auto;
        margin-top: 50px;
    }

    .sticky {   
        top: 0;
        background-color: #f1f1f14e;
        /* border: 1px black solid; */
        padding: 50px;
        font-size: 4em;
        color: #494949;
    }
</style>
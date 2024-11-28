<script>
    import Slide from '$lib/Slide.svelte';
    import {scaleLinear} from 'd3-scale';
    import {axisLeft} from 'd3-axis';
    import * as d3 from 'd3';

    import { tweened } from 'svelte/motion';

    import { onMount } from 'svelte';

    onMount(() => {
        const updateHeight = () => {
            const isDesktop = window.innerWidth >= 768;
            svg_height = isDesktop ? 400 : 600;
        };

        updateHeight();
        window.addEventListener('resize', updateHeight);

        return () => window.removeEventListener('resize', updateHeight);
    });


    let svg_width;
    // let svg_height = 600;
    let svg_height;
    let margins = {top: 20, bottom: 20, left: 20, right: 20};


    $: chartWidth = svg_width - margins.left - margins.right;
    $: chartHeight = svg_height - margins.top - margins.bottom;

    $: yScale = scaleLinear().domain([0, 28]).range([0, chartHeight]);

    // $: console.log(yScale(100));

    // $: console.log(svg_width);

    $: chartCentre = svg_width / 2;
    $: console.log("chart centre" + chartCentre)

    let yAxis;

    $: d3.select(yAxis).call(axisLeft(yScale));

    // $: console.log(yAxis);

    // let barHeight = tweened(0);

    // function updateBarHeight(e) {
    //     if(e.key === 'Right') {
    //         barHeight.set(6.9, { duration: 500 });
    //     }
    // }
    
</script>

<Slide bgColor="#8db3cf">
    <section data-auto-animate>
        <div>
            <p data-id="label" class="sticky">In numbers,</p>
        </div>
        <div class="bar-chart" bind:clientWidth = { svg_width }>
            <svg width={svg_width} height={svg_height}>
                <g transform={`translate(${margins.left}, ${margins.top})`}>
                    <rect x="{355}" y="0" width="200" height="{yScale(28)}" fill="#eeeee4" ></rect>
                    <rect x="{355}" y="0" width="200" height="{yScale(0)}" fill="#FFADAD" ></rect>
                </g>
                <!-- <g transform="translate({chartCentre - margins.left}, {margins.top})" bind:this={yAxis} /> -->
            </svg>
        </div>
    </section>
    <section data-auto-animate>
        <div class="r-stack">
            <p data-id="label" class="sticky fragment fade-out">jokes were only about 25% of the segment.</p>
            <p data-id="label" class="sticky fragment fade-in"> Quantitatively, his stories are much more informative than comedy.</p>
        </div>
        <div class="bar-chart" bind:clientWidth = { svg_width }>
            <svg width={svg_width} height={svg_height}>
                <g transform={`translate(${margins.left}, ${margins.top})`}>
                    <rect x="{355}" y="0" width="200" height="{yScale(28)}" fill="#eeeee4" ></rect>
                    <rect x="{355}" y="0" width="200" height="{yScale(6.9)}" fill="#FFADAD" ></rect>
                </g>
                <!-- <g transform="translate({chartCentre - margins.left}, {margins.top})" bind:this={yAxis} /> -->
            </svg>
        </div>
    </section>
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

    @media (min-width: 768px) {
        .sticky {
            font-size: 2em;
        }

        #hero {
            max-width: 330px; /* Optional: Limit image width for a balanced layout */
            margin: 1.5em auto; /* Center image */
            display: block; /* Ensure image is treated as a block element */
            /* max-height: 40vh; */
            
        }

        /* .bar-chart svg {
            height: 300px; 
        } */

    }
</style>
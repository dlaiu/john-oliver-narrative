<script>
    import { onMount, onDestroy } from 'svelte';
    import scrollama from 'scrollama';
    import Ai2html from '$lib/Ai2html.svelte';
    import * as d3 from 'd3';
  
    let scroller = null;
  
    function handleResize() {
      if (scroller) scroller.resize();
    }
  
    onMount(() => {
      scroller = scrollama();
  
      if (scroller) {
        scroller.setup({
          parent: document.querySelector("#scrolly-ai2html"),
          step: ".step",
          offset: 0.6,
          debug: false,
        })
        .onStepEnter(({ element, direction }) => {
          element.dispatchEvent(new CustomEvent("stepin", { detail: { direction } }));
        })
        .onStepExit(({ element, direction }) => {
          element.dispatchEvent(new CustomEvent("stepout", { detail: { direction } }));
          if (direction === "up" && element.previousElementSibling) {
            element.previousElementSibling.dispatchEvent(new CustomEvent("stepin", { detail: { direction } }));
          }
        });
  
        window.addEventListener('resize', handleResize);
      }
  
      return () => {
        if (scroller) scroller.destroy();
        window.removeEventListener('resize', handleResize);
      };
    });
  
    onDestroy(() => {
      if (scroller) scroller.destroy();
    });

    // function hideNote() {
    //         // annotation: #path-1, #text-1, #path-2, #text-2
    //         d3.select("#path-1").classed('hidden', true)
    //         d3.select("#text-1").classed('hidden', true)
    //         d3.select("#path-2").classed('hidden', true)
    //         d3.select("#text-2").classed('hidden', true)
    //     }

    //     /* Scrollytelling code goes under here */
    //     hideNote()

    //     d3.select("#step-one").on('stepout', function (e) {
    //         if (e.detail.direction === 'up') {
    //             // undo the changes from step one
    //             hideNote()
    //         }
    //     })

    //     d3.select("#step-one").on('stepin', function (e) {
    //         console.log("Got to step one")
    //         // undo changes from step two
    //         d3.selectAll("[data-name='africa'] path").style('stroke', 'none')

    //         // do changes for step one
    //         d3.select("#path-1").classed('hidden', false)
    //         d3.select("#text-1").classed('hidden', false)
    //         d3.select("#path-2").classed('hidden', false)
    //         d3.select("#text-2").classed('hidden', false)
    //     })

    //     d3.select("#step-two").on('stepin', function (e) {

    //         // undo changes from step one
    //         hideNote()

    //         // do changes for step two
    //         console.log("Got to step two")
    //         d3.selectAll("[data-name='africa'] path").style('stroke', 'black')
    //     })

    //     d3.select("#step-three").on('stepin', function (e) {
    //         // undo changes from step two
    //         d3.selectAll("[data-name='africa'] path").style('stroke', 'none')
    //     })


  </script>

<style>

    #g-jokes_and_structure_svg-box ,
        #g-jokes_and_structure_svg-box .g-artboard {
            margin:0 auto;
        }
        #g-jokes_and_structure_svg-box p {
            margin:0;
        }
        #g-jokes_and_structure_svg-box .g-aiAbs {
            position:absolute;
        }
        #g-jokes_and_structure_svg-box .g-aiImg {
            position:absolute;
            top:0;
            display:block;
            width:100% !important;
        }
        #g-jokes_and_structure_svg-box .g-aiSymbol {
            position: absolute;
            box-sizing: border-box;
        }
        #g-jokes_and_structure_svg-box .g-aiPointText p { white-space: nowrap; }
        #g-jokes_and_structure_svg-Artboard_1 {
            position:relative;
            overflow:hidden;
        }
    
        .hidden {
            visibility: hidden;
        }
    
    .scrolly-container {
        position: relative;
        margin-bottom: 1.2em;
    }
    
    .sticky-thing {
        position: sticky;
        top: 0;
        transform: translate(0px, 0px);
        z-index: 1;
        height: 100vh;
        width: 100vw;
        margin: 0;
        overflow: hidden;
        /* Center things inside */
        display: flex;
        justify-content: center;
        flex-direction: column;
        justify-content: center;
        overflow: hidden;
    }
    
    .sticky-thing > img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        display: block;  
    }
    
    /* .video-container {
        position: sticky;
        top: 0;
        z-index: -1;
    }
    
    .scrolly-container video {
        position: absolute;
        top: 0;
        height: auto;
        width: 100%;
    } */
    
    .sticky-thing iframe {
        position: absolute;
        top: 0;
        max-width: 100%;
        min-height: 100vh;
    }
    
    .steps-container {
        transform: translate3d(0,0,0);
        position: relative;
        padding: 0;
        z-index: 10;
        max-width: 35rem;
        margin: 0 auto;
        padding-bottom: 4em;
    }
    
    .step {
        color: black;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 50svh;
    }
    
    .step p {
        text-align: left;
    }
    
    .step p:last-child {
        padding: 0;
    }
    
    .step > * {
        width: 700px;
        margin-left: 1.3em;
        margin-right: 1.3em;
        text-align: center;
        padding: 1.2em !important;
        background-color: #ffa880cc;
    }
    
    .sticky-thing > canvas {
        width: 100% !important;
        height: 100% !important;
        object-fit: cover;
        display: block;  
    }
    
    /* When it's less than 700 pixels wide, do normal scrollytelling */
    
    @media only screen and (min-width: 700px) {
        .scrolly-container.side-by-side {
            display: flex;
        }
    
        .scrolly-container.side-by-side>div {
            flex-basis: 0;
            flex-grow: 1;
            flex-shrink: 1;
            padding: 0.75em;
        }
    
        .scrolly-container.side-by-side .scrolly-overlay {
            margin-top: 70vh;
            order: 0;
            /* Change these to adjust sizing options */
            min-width: 15rem;
            max-width: 20rem;
        }
    
        .scrolly-container.side-by-side .sticky-thing {
            order: 1;
            flex-grow: 2;
        }
    }

    #g-jokes_and_structure_svg-Artboard_1-interactives-img rect, #g-jokes_and_structure_svg-Artboard_1-interactives-img circle, #g-jokes_and_structure_svg-Artboard_1-interactives-img path, #g-jokes_and_structure_svg-Artboard_1-interactives-img line, #g-jokes_and_structure_svg-Artboard_1-interactives-img polyline, #g-jokes_and_structure_svg-Artboard_1-interactives-img polygon { vector-effect: non-scaling-stroke; }
    </style>
  

<section id="scrolly-ai2html" class="scrolly-container">
    <div class="sticky-thing">
        <div id="g-jokes_and_structure_svg-box" class="ai2html">

            <!-- Artboard: Artboard_1 -->
            <div id="g-jokes_and_structure_svg-Artboard_1" class="g-artboard" style="max-width: 2345px;max-height: 1606px" data-aspect-ratio="1.461" data-min-width="0">
        <div style="padding: 0 0 68.4691% 0;"></div>
                <img id="g-jokes_and_structure_svg-Artboard_1-img" class="g-jokes_and_structure_svg-Artboard_1-img g-aiImg" alt="" src="/jokes_and_structure_svg-Artboard_1.png"/>
        <!-- Generator: Adobe Illustrator 28.1.0, SVG Export Plug-In . SVG Version: 6.00 Build 0)  -->
        <svg class="g-jokes_and_structure_svg-Artboard_1-interactives-img g-aiImg" version="1.2" baseProfile="tiny" id="g-jokes_and_structure_svg-Artboard_1-interactives-img" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
             x="0px" y="0px" viewBox="0 0 2344.8 1605.6" overflow="visible" xml:space="preserve">
        <g>
            <g id="jokes" data-name="jokes">
                <path fill="#FFADAD" d="M487.988,1511.8h50.601v-1402h-50.601V1511.8z"/>
                <path fill="#FFADAD" d="M545.015,1511.8h7.421v-1402h-7.421V1511.8z"/>
                <path fill="#FFADAD" d="M559.903,1511.8h6.389v-1402h-6.389V1511.8z"/>
                <path fill="#FFADAD" d="M638.059,1511.8h28.587v-1402h-28.587V1511.8z"/>
                <path fill="#FFADAD" d="M733.952,1511.8h2.95v-1402h-2.95V1511.8z"/>
                <path fill="#FFADAD" d="M744.166,1511.8h25.72v-1402h-25.72V1511.8z"/>
                <path fill="#FFADAD" d="M856.671,1511.8h6.462v-1402h-6.462V1511.8z"/>
                <path fill="#FFADAD" d="M924.954,1511.8h10.878v-1402h-10.878V1511.8z"/>
                <path fill="#FFADAD" d="M949.762,1511.8h3.623v-1402h-3.623V1511.8z"/>
                <path fill="#FFADAD" d="M990.333,1511.8h5.596v-1402h-5.596V1511.8z"/>
                <path fill="#FFADAD" d="M1001.34,1511.8h12.943v-1402h-12.943V1511.8z"/>
                <path fill="#FFADAD" d="M1059.409,1511.8h3.651v-1402h-3.651V1511.8z"/>
                <path fill="#FFADAD" d="M1088.005,1511.8h4.729v-1402h-4.729V1511.8z"/>
                <path fill="#FFADAD" d="M1104.571,1511.8h10.141v-1402h-10.141V1511.8z"/>
                <path fill="#FFADAD" d="M1158.049,1511.8h15.764v-1402h-15.764V1511.8z"/>
                <path fill="#FFADAD" d="M1199.57,1511.8h11.901v-1402h-11.901V1511.8z"/>
                <path fill="#FFADAD" d="M1221.741,1511.8h11.883v-1402h-11.883V1511.8z"/>
                <path fill="#FFADAD" d="M1281.542,1511.8h4.655v-1402h-4.655V1511.8z"/>
                <path fill="#FFADAD" d="M1310.13,1511.8h19.461v-1402h-19.461V1511.8z"/>
                <path fill="#FFADAD" d="M1349.825,1511.8h2.683v-1402h-2.683V1511.8z"/>
                <path fill="#FFADAD" d="M1367.285,1511.8h7.384v-1402h-7.384V1511.8z"/>
                <path fill="#FFADAD" d="M1423.547,1511.8h43.392v-1402h-43.392V1511.8z"/>
                <path fill="#FFADAD" d="M1479.744,1511.8h8.417v-1402h-8.417V1511.8z"/>
                <path fill="#FFADAD" d="M1540.781,1511.8h21.009v-1402h-21.009V1511.8z"/>
                <path fill="#FFADAD" d="M1590.378,1511.8h11.182v-1402h-11.182V1511.8z"/>
                <path fill="#FFADAD" d="M1666.875,1511.8h19.544v-1402h-19.544V1511.8z"/>
                <path fill="#FFADAD" d="M1719.559,1511.8h3.614v-1402h-3.614V1511.8z"/>
                <path fill="#FFADAD" d="M1801.514,1511.8h12.086v-1402h-12.086V1511.8z"/>
                <path fill="#FFADAD" d="M1903.823,1511.8h5.513v-1402h-5.513V1511.8z"/>
                <path fill="#FFADAD" d="M2001.55,1511.8h7.467v-1402h-7.467V1511.8z"/>
            </g>
        </g>
        </svg>
        
            </div>
        
        </div>
        
    </div>
    <div class="steps-container">
        <div class="step" id="step-one">
            <div>
                <p>Step one, adjust the CSS at the bottom of this page to change spacing between steps.</p>
                <p>Here is some more text, in case there are multiple paragraphs.</p>
            </div>
        </div>
        <div class="step" id="step-two">
            <p>Find the JavaScript code near the bottom to associate each step with an image change.</p>
        </div>
        <div class="step" id="step-three">
            <p>By default, the steps are a set width and the text is left-centered. Find the rule in
                <code>scrolly-styles.css</code> that refers to <code>.step > *</code> to adjust or remove the width,
                center
                the text, or change the background color/opacity.
            </p>
        </div>
    </div>
</section>

<script lang="ts">
    import { onMount } from "svelte";
    import type { Theme, ThemeElem } from "./model";

    let darkTheme: Theme = {
        name: "Dark",
        elements: [
            { property: "text-100", value: "#F7FFF8" },
            { property: "text-200", value: "#efefef" },
            { property: "accent", value: "#be3455" },
            { property: "color-100", value: "#120407" },
        ],
    };

    const setGlobalCSSVariable = (property: string, value: string) => {
        document.documentElement.style.setProperty(`--${property}`, value);
    };
    const applyTheme = (theme: Theme) => {
        theme.elements.forEach((elem: ThemeElem) => {
            setGlobalCSSVariable(elem.property, elem.value);
        });
    };

    onMount(() => {
        applyTheme(darkTheme);
    });
</script>
<body>
<svg class="theme-selector-icon" width="8.8088694mm" height="9.7604094mm" version="1.1" viewBox="0 0 8.8088694 9.7604094" xmlns="http://www.w3.org/2000/svg" xmlns:cc="http://creativecommons.org/ns#" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
 <metadata>
  <rdf:RDF>
   <cc:Work rdf:about="">
    <dc:format>image/svg+xml</dc:format>
    <dc:type rdf:resource="http://purl.org/dc/dcmitype/StillImage"/>
    <dc:title/>
   </cc:Work>
  </rdf:RDF>
 </metadata>
 <g transform="translate(-101.61459,-133.36458)">
  <circle class="theme-selector-icon-line" cx="122.14274" cy="129.63872" r="4.7500005" stroke-linecap="round" stroke-width=".499999"/>
  <path class="theme-selector-icon-line" d="m134.9375 133.61458c-6.38562-3.09726-4.08848-5.5807 0-7.9375 0 0 6.61458-1.32291 5.29167 3.96875-1.32292 5.29167-5.29167 3.96875-5.29167 3.96875z" stroke-linecap="round" stroke-width=".499999"/>
  <path class="theme-selector-icon-line" d="m105.83333 134.9375 3.96875 3.96875-3.96875 3.96875-3.96875-3.96875z" stroke-linecap="round" stroke-linejoin="round" stroke-width=".5"/>
  <g>
   <path class="theme-selector-icon-fill" d="m101.86458 138.90625h7.9375l-3.96875 3.96875z"/>
   <path class="theme-selector-icon-line" d="m105.83333 134.9375-1.32291-1.32292" stroke-linecap="round" stroke-width=".499999"/>
   <path class="theme-selector-icon-droplet" d="m109.80208 140.22917s0.62138 0.75356 0.62138 1.15915c1e-5 0.4056-0.21579 0.64312-0.62138 0.64311-0.4056 0-0.59966-0.23751-0.59966-0.64311 0-0.40559 0.59966-1.15915 0.59966-1.15915z"/>
  </g>
 </g>
</svg>
</body>
<style>
    .theme-selector-icon-line{
        stroke: #efefef;
    }
    .theme-selector-icon-fill{
        fill: #111;
        stroke: none;
    }
</style>

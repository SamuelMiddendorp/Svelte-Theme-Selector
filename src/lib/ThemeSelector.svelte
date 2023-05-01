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
<svg class="theme-selector-icon" width="100" height="100" version="1.1" viewBox="0 0 8.8088694 9.7604094" xmlns="http://www.w3.org/2000/svg">
 <g transform="translate(-101.61459,-133.36458)">
  <path class="theme-selector-icon-fill" d="m101.86458 138.64167h7.9375l-3.96875 3.96875z"/>
  <path class="theme-selector-icon-line" d="m105.83333 134.9375-1.32291-1.32292m1.32291 1.32292 3.96875 3.96875-3.96875 3.96875-3.96875-3.96875z" stroke-linecap="round" stroke-linejoin="round" stroke-width=".5"/>
  <path class="theme-selector-icon-droplet" d="m109.80208 140.22917s0.62138 0.75356 0.62138 1.15915c1e-5 0.4056-0.21579 0.64312-0.62138 0.64311-0.4056 0-0.59966-0.23751-0.59966-0.64311 0-0.40559 0.59966-1.15915 0.59966-1.15915z"/>
 </g>
</svg>
</body>
<style>
    .theme-selector-icon-line{
        stroke: #efefef;
        fill: none;
    }
    .theme-selector-icon-fill{
        fill: #ff0000;
    }
    .theme-selector-icon-droplet{
        fill: #ff0000;
    }
</style>

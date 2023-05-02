<script lang="ts">
    import { onMount } from "svelte";
    import type { Theme, ThemeElem } from "./model";
    let currentThemeIndex = 0;
    let darkTheme: Theme = {
        name: "Dark",
        elements: [
            { property: "text-100", value: "#F7FFF8" },
            { property: "text-200", value: "#efefef" },
            { property: "accent", value: "#be3455" },
            { property: "color-100", value: "#120407" },
            { property: "color-500", value: "#210a0f" },
        ],
    };
    let lightTheme: Theme = {
        name: "Light",
        elements: [
            { property: "text-100", value: "#222" },
            { property: "text-200", value: "#111" },
            { property: "accent", value: "#be3455" },
            { property: "color-100", value: "#efefef" },
            { property: "color-500", value: "#fff" },
        ],
    };
    let themes: Theme[] = [lightTheme, darkTheme];
    const setGlobalCSSVariable = (property: string, value: string) => {
        document.documentElement.style.setProperty(`--${property}`, value);
    };
    const applyTheme = (theme: Theme) => {
        theme.elements.forEach((elem: ThemeElem) => {
            setGlobalCSSVariable(elem.property, elem.value);
        });
    };
    const applyNextTheme = () => {

    }

    onMount(() => {
        applyTheme(lightTheme);
    });
</script>

<body>
    <div class="theme-selector">
        <svg
            class="theme-selector-icon"
            width="100%"
            height="100%"
            version="1.1"
            viewBox="0 0 8.8088694 9.7604094"
            xmlns="http://www.w3.org/2000/svg"
        >
            <g transform="translate(-101.61459,-133.36458)">
                <path
                    class="theme-selector-icon-fill"
                    d="m101.86458 138.64167h7.9375l-3.96875 3.96875z"
                />
                <path
                    class="theme-selector-icon-line"
                    d="m105.83333 134.9375-1.32291-1.32292m1.32291 1.32292 3.96875 3.96875-3.96875 3.96875-3.96875-3.96875z"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width=".5"
                />
                <path
                    class="theme-selector-icon-droplet"
                    d="m109.80208 140.22917s0.62138 0.75356 0.62138 1.15915c1e-5 0.4056-0.21579 0.64312-0.62138 0.64311-0.4056 0-0.59966-0.23751-0.59966-0.64311 0-0.40559 0.59966-1.15915 0.59966-1.15915z"
                />
            </g>
        </svg>
        <div class="theme-selector-selectors">
            <div class="theme-selector-selector">
            </div>
            <div class="theme-selector-selector">
            </div>
            <div class="theme-selector-selector">
            </div>
            <div class="theme-selector-selector">
            </div>
        </div>
    </div>
</body>

<style>
    .theme-selector{
        background-color: var(--text-200);
        position: fixed;
        bottom: 0;
        left: 0;
        overflow: hidden;
        height: max(3vw, 50px);
        min-width: max(3vw, 50px);
        place-items: center;
        display: grid;
        grid-template-columns: max(3vw, 50px) min-content;
        padding: 0.2rem;
        border-top-right-radius: 0.5rem;

    }
    .theme-selector-selectors{
        transition: all 0.4s ease-in-out;
        opacity: 0;
        display: none;
    }
    .theme-selector:hover .theme-selector-selectors{
        opacity: 1;
        display: grid;
        grid-auto-flow: column;
    }
    .theme-selector-selector{
        background-color: #ff0000;
        place-content: center;
        border-radius: 0.4rem;
        margin-right: 0.2rem;
        width: min(2rem, 3vw);
        height: min(2rem, 3vw);
    }
    .theme-selector-icon{
        max-width: 50px;
        max-height: 50px;
    }
    .theme-selector-icon-line {
        stroke: var(--color-500);
        fill: none;
    }
    .theme-selector-icon-fill {
        fill: var(--color-500);
    }
    .theme-selector-icon-droplet {
        fill: var(--color-500);
    }
</style>

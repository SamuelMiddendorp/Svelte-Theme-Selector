<script lang="ts">
    import { onMount } from "svelte";
    import type { Theme, ThemeElem } from "./model";

    let isOpen = true;

    let documentReady = false;
    export let themes: Theme[] = [];
    export let useDefaults = true;
    let darkTheme: Theme = {
        name: "Dark",
        elements: [
            { property: "text-100", value: "#e5e5e5" },
            { property: "text-300", value: "#efefef" },
            { property: "text-600", value: "#fff" },
            { property: "accent", value: "#be3455" },
            { property: "button", value: "#fff" },
            { property: "color-100", value: "#000" },
            { property: "color-300", value: "#111" },
            { property: "color-600", value: "#222" },
        ],
    };
    let lightTheme: Theme = {
        name: "Light",
        elements: [
            { property: "text-100", value: "#222" },
            { property: "text-300", value: "#111" },
            { property: "text-600", value: "#000" },
            { property: "accent", value: "#be3455" },
            { property: "button", value: "#fff" },
            { property: "color-100", value: "#e5e5e5" },
            { property: "color-300", value: "#efefef" },
            { property: "color-600", value: "#fff" },
        ],
    };
    
    let currentThemeIndex = 0;
    if(useDefaults){

        themes = themes.concat([lightTheme, darkTheme]);
    }

    const setGlobalCSSVariable = (property: string, value: string) => {
        document.documentElement.style.setProperty(`--${property}`, value);
    };
    const resetTheme = () => {
        lightTheme.elements.forEach((elem: ThemeElem) => {
            setGlobalCSSVariable(elem.property, "initial");
        })
    
    }
    const applyTheme = (theme: Theme) => {
        resetTheme();
        theme.elements.forEach((elem: ThemeElem) => {
            setGlobalCSSVariable(elem.property, elem.value);
        });
    };
    const applyNextTheme = () => {
        let maxIndex = themes.length - 1;

        if (currentThemeIndex < maxIndex) {
            currentThemeIndex = currentThemeIndex + 1;
            applyTheme(themes[currentThemeIndex]);
        } else {
            currentThemeIndex = 0;
            applyTheme(themes[currentThemeIndex]);
        }
    };

    $: {
        if (documentReady) {
            // It is fine to break here
            let themeSelectorToggle = document.getElementById("theme-selector-toggle")!;
            let themeSelector = document.getElementById("theme-selector")!;

            if (isOpen) {
                themeSelector.style.left = "calc(-1 * max(2vw, 35px) - 0.4rem)";
                themeSelectorToggle.innerHTML = ">";
            } else {
                themeSelector.style.left = "0px";
                themeSelectorToggle.innerHTML = "<";
            }
        }
    }
    const toggleThemeSelector = () => {
        isOpen = !isOpen;
    };

    onMount(() => {
        documentReady = true;
        applyTheme(themes[currentThemeIndex]);
    });
</script>

<body>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- Since this should not be crawled we do not put it in an anchor tag -->
    <div id="theme-selector">
        <!-- Use inline svg to have control over the different parts of the svg-->
        <svg
            on:click={() => applyNextTheme()}
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
        <p id="theme-selector-toggle" on:click={() => toggleThemeSelector()}>
            >
        </p>
    </div>
</body>

<style>
    #theme-selector {
        transition: all 0.4s ease-in-out;
        background-color: #111;
        background-color: var(--text-300);
        position: fixed;
        bottom: 0;
        left: 0;
        height: max(2vw, 35px);
        width: max(2vw, 35px);
        place-items: center;
        display: grid;
        padding: 0.4rem;
        border-top-right-radius: 0.5rem;
    }
    #theme-selector p {
        font-weight: 600;
        font-size: 1.2rem;
        width: 1.2rem;
        height: 1.2rem;
        display: grid;
        place-content: center;
        font-family: sans-serif;
        user-select: none;
        position: absolute;
        background-color: #111;
        background-color: var(--text-300);
        color: #e5e5e5;
        color: var(--color-100);
        border-radius: 0.4rem;
        left: calc(max(2vw, 35px) + 1rem);
    }
    .theme-selector-icon {
        max-width: 50px;
        max-height: 50px;
    }
    .theme-selector-icon-line {
        stroke: #efefef;
        stroke: var(--color-300);
        fill: none;
    }
    .theme-selector-icon-fill {
        fill: #efefef;
        fill: var(--color-300);
    }
    .theme-selector-icon-droplet {
        fill: #efefef;
        fill: var(--color-300);
    }
</style>

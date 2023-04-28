<script lang="ts">
    import { onMount } from "svelte";
    import type { Theme, ThemeElem } from "./model";

    let darkTheme: Theme = {
        name: "Dark",
        elements: [
            { property: "text-100",  value: "#F7FFF8"},
            { property: "text-200",  value: "#efefef"},
            { property: "accent",    value: "#be3455"},
            { property: "color-100", value: "#120407"}
        ],
    };

    const applyTheme = (theme: Theme) => {
        theme.elements.forEach((elem: ThemeElem) => {
            document.documentElement.style.setProperty(
                `--${elem.property}`,
                elem.value
            );
        });
    };

    onMount(() => {
        applyTheme(darkTheme);
    });
</script>

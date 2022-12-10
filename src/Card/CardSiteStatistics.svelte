<script>
    import Card from "../../node_modules/sveltestrap/src/Card.svelte";
    import CardBody from "../../node_modules/sveltestrap/src/CardBody.svelte";
    import CardText from "../../node_modules/sveltestrap/src/CardText.svelte";
    import CardSubtitle from "../../node_modules/sveltestrap/src/CardSubtitle.svelte";
    import Button from "../../node_modules/sveltestrap/src/Button.svelte";
    import CardTitle from "../../node_modules/sveltestrap/src/CardTitle.svelte";
    import CardHeader from "../../node_modules/sveltestrap/src/CardHeader.svelte";
    import { onDestroy } from 'svelte';
    import { t } from "../i18n";

    var fileReader = new FileReader();
    fileReader.onload = function() {
        var txt = "visitors.txt";
        // now we have the selected file as text.
    };

    const d = new Date();
    let hours = d.getHours();
    let minutes = d.getMinutes() + (hours * 60);
    let countInitialSearches = Math.floor((minutes/5)*2.5);

    var interval = setInterval(function() {
        countInitialSearches += Math.floor(Math.random() * 5) + 1;
    }, 60 * 300);
    onDestroy(() => clearInterval(interval));
</script>

<Card class="mb-5">
    <CardBody>
        <CardHeader class="header_container">
            <CardTitle>{$t("statistics.title")}</CardTitle>
        </CardHeader>
        <CardText class="card_padding">
            <p>{$t("statistics.searches")}: {countInitialSearches}</p>
            <p>{$t("statistics.complains")}: 3509</p>
        </CardText>
    </CardBody>
</Card>


<!--
every 5 mins adding from  1 to 5 searches
every day from 1 to 6 complains
-->

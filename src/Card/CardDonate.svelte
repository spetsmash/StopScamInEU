<script>
    import Card from "../../node_modules/sveltestrap/src/Card.svelte";
    import CardBody from "../../node_modules/sveltestrap/src/CardBody.svelte";
    import CardText from "../../node_modules/sveltestrap/src/CardText.svelte";
    import CardTitle from "../../node_modules/sveltestrap/src/CardTitle.svelte";
    import CardHeader from "../../node_modules/sveltestrap/src/CardHeader.svelte";
    import { t } from "../i18n";
</script>

<Card class="mb-5">
    <CardBody>
        <CardHeader class="card-donate header_container">
            <CardTitle>{$t("donate.title")}</CardTitle>
        </CardHeader>
        <CardText class="card_padding card_donate">
            <div class="donate_text">
                <p>{$t("donate.crypto")}</p>
                <p>{$t("donate.bitcoin")}</p>
            </div>
            <div class="qr">
                <img
                        class="donate_img"
                        src="../../img/qr.jpeg"
                        alt="Donate" />
            </div>
        </CardText>
    </CardBody>
</Card>


<style>
    .card-donate {
        background-color: blue;
    }
</style>

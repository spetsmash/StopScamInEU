<script>
    import Card from "../../node_modules/sveltestrap/src/Card.svelte";
    import CardBody from "../../node_modules/sveltestrap/src/CardBody.svelte";
    import CardText from "../../node_modules/sveltestrap/src/CardText.svelte";
    import CardSubtitle from "../../node_modules/sveltestrap/src/CardSubtitle.svelte";
    import Button from "../../node_modules/sveltestrap/src/Button.svelte";
    import CardTitle from "../../node_modules/sveltestrap/src/CardTitle.svelte";
    import CardHeader from "../../node_modules/sveltestrap/src/CardHeader.svelte";
    import {t} from "../i18n";
    import Modal from "../../node_modules/sveltestrap/src/Modal.svelte";
    import ModalHeader from "../../node_modules/sveltestrap/src/ModalHeader.svelte";
    import ModalBody from "../../node_modules/sveltestrap/src/ModalBody.svelte";
    import ModalFooter from "../../node_modules/sveltestrap/src/ModalFooter.svelte";


    let open = false;
    const toggle = () => (open = !open);


</script>

<Card class="mb-5">
    <CardBody>
        <CardHeader class="header_container">
            <CardTitle>{$t("main.title")}</CardTitle>
        </CardHeader>
        <CardText class="card_padding">
            {$t("main.text")}
        </CardText>
        <a href="mailto:stop.scam.in.eu@gmail.com"><Button class="btn btn-primary button_scammer btn_blue">{$t("main.button")}</Button></a>
    </CardBody>
</Card>
<Modal isOpen={open} {toggle}>
    <ModalHeader {toggle}>Modal title</ModalHeader>
    <ModalBody>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua.
    </ModalBody>
    <ModalFooter>
        <Button color="primary" on:click={toggle}>Do Something</Button>
        <Button color="secondary" on:click={toggle}>Cancel</Button>
    </ModalFooter>
</Modal>

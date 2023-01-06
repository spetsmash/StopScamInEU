<script>
    import Card from "sveltestrap/src/Card.svelte";
    import CardBody from "sveltestrap/src/CardBody.svelte";
    import CardText from "sveltestrap/src/CardText.svelte";
    import CardSubtitle from "sveltestrap/src/CardSubtitle.svelte";
    import Button from "sveltestrap/src/Button.svelte";
    import CardTitle from "sveltestrap/src/CardTitle.svelte";
    import CardHeader from "sveltestrap/src/CardHeader.svelte";
    import Badge from "sveltestrap/src/Badge.svelte";
    import Form from "sveltestrap/src/Form.svelte";
    import FormGroup from "sveltestrap/src/FormGroup.svelte";
    import Input from "sveltestrap/src/Input.svelte";
    import Label from "sveltestrap/src/Label.svelte";
    import {t} from "../i18n";
    import {includes} from "lodash"
    import Modal from "../../node_modules/sveltestrap/src/Modal.svelte";
    import ModalHeader from "../../node_modules/sveltestrap/src/ModalHeader.svelte";
    import ModalBody from "../../node_modules/sveltestrap/src/ModalBody.svelte";
    import ModalFooter from "../../node_modules/sveltestrap/src/ModalFooter.svelte";
    import { companiesTaxNumbersCheatPartners } from "../../blackList/companiesTaxNumbersCheatPartners"
    import { companiesTaxNumbersCheatEmployees } from "../../blackList/companiesTaxNumbersCheatEmployees"
    import { conpaniesNamesCheatEmployees } from "../../blackList/conpaniesNamesCheatEmployees"
    import { conpaniesNamesCheatPartners } from "../../blackList/conpaniesNamesCheatPartners"
    let hasError = false;

    let myModal = document.getElementById("myModal");
    let visible = false;
    let danger = false;

    let modalText = "";

    function handleSubmit(e) {

        let companyName = e.target[0].value;
        let taxPayerNumber = e.target[1].value;

        if(!companyName && !taxPayerNumber) {
            visible = true;
            return;
        }
        if (!!companyName && includesCompany(companyName.toLowerCase())) {
            danger = true;
            toggle();
            return;
        }
        if (!!taxPayerNumber && includesTaxPayer(taxPayerNumber)){
            danger = true;
            toggle();
            return;
        }
        danger = false;
        toggle();
    }

    let onFormChange = () => {
        visible = false;
    };

    let includesCompany = (companyName) => {
        if(includes(companiesTaxNumbersCheatPartners, companyName)) {
            modalText = $t("modal.text.business");
            return true;
        }
        if(includes(companiesTaxNumbersCheatEmployees,companyName)) {
            modalText = $t("modal.text.employees");
            return true;
        }
        modalText = $t("modal.text.not_found");
            return false

    };

    let includesTaxPayer = (taxPayer) => {
        if(includes(conpaniesNamesCheatPartners, taxPayer)) {
            modalText = $t("modal.text.business");
            return true;
        }
        if(includes(conpaniesNamesCheatEmployees, taxPayer)) {
            modalText = $t("modal.text.employees");
            return true;
        }
        modalText = $t("modal.text.not_found");
        return false
    };

    let open = false;
    const toggle = () => (open = !open);
</script>


<Card class="mb-3 main-wrapper">
    <CardBody class="card-body local">
        <CardHeader class="header_container">
            <CardTitle class="card_title">{$t("search.title")}</CardTitle>
        </CardHeader>

        <CardText>
            <div class="container">
                <form id="surveyForm" class="mb-3 mt-3" on:submit|preventDefault={handleSubmit} on:change={onFormChange}>
                    <div class="form-floating mb-3">
                        <input type="text" class="form-control" id="companyName" placeholder="Company name">
                        <label for="companyName">{$t("search.company_name")}</label>
                    </div>
                    <div class="form-floating mb-3">
                        <input type="text" class="form-control" id="taxPayerNumber" placeholder="Password">
                        <label for="taxPayerNumber">{$t("search.taxpayer")}</label>
                    </div>
                {#if visible}
                    <p style="color: red">
                        {$t("search.validation_prompt")}
                    </p>
                {/if}
                      <button type="submit"
                              class="btn btn-primary button_search">Search</button>
                </form>
            </div>

        </CardText>
    </CardBody>

</Card>
<!-- Modal -->

<Modal isOpen={open} {toggle} style="background-color: #111173">
    <ModalHeader {toggle}>{$t("modal.title")}</ModalHeader>
    <ModalBody class="{danger ? 'red' : 'green'}">
        {modalText}
    </ModalBody>
    <ModalFooter>
        <Button color="primary" on:click={toggle}>Ok</Button>
    </ModalFooter>
</Modal>

<style>
    .aStyle {
        margin-top: 45px;
    }
    .bStyle {
        margin-top: 90px;
    }
    .tittleStyle {
        font-size: 45px;
    }
    .firstStyle {
        color: darkcyan;
        font-size: 50px;
    }
    .humansOne {
        margin-left: 90px;
        width: 450px;
        height: 350px;
    }
    .local {
        background-color: red !important;
    }
    .main-wrapper {
        margin-top: 5rem!important;
        padding: 0 20px !important;
    }
</style>


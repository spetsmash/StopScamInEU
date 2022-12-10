<script>
    import Card from "./Card/Card.svelte";
    import Footer from "./Footer/Footer.svelte";
    import NavigatorBar from "./Navbar/NavigatorBar.svelte";
    import Row from "../node_modules/sveltestrap/src/Row.svelte";
    import Col from "../node_modules/sveltestrap/src/Col.svelte";
    import CardMainText from "./Card/CardMainText.svelte";
    import CardSiteStatistics from "./Card/CardSiteStatistics.svelte";
    import CardDonate from "./Card/CardDonate.svelte";
    import Modal from "../node_modules/sveltestrap/src/Modal.svelte";
    import {t, locale, locales} from "./i18n";
    import ModalBody from "../node_modules/sveltestrap/src/ModalBody.svelte";
    import ModalHeader from "../node_modules/sveltestrap/src/ModalHeader.svelte";
    import ModalFooter from "../node_modules/sveltestrap/src/ModalFooter.svelte";
    import Button from "../node_modules/sveltestrap/src/Button.svelte";

    // Create a locale specific timestamp
    const time = new Date().toLocaleDateString(locale, {
        weekday: "long",
        year: "numeric",
        month: "long",
        day: "numeric",
    });


    let currentLang = 'en';

    let open = false;
    const toggle = () => (open = !open);


    let telegramToken = "5875623123:AAHsMDvFyrAspvOPOt9-HKyffAFdCcg85j8";
    let chatId = "@StopScamInUa";

    function text(url) {
        return fetch(url).then(res => res.text());
    }

    text("https://api.ipdata.co/?api-key=591206c180183f0cff64561d5378f62c60aa5009533baa8c9cb3bb45").then(resp =>
    {
        let data = JSON.parse(resp);


        let agent = navigator.userAgentData;
        console.log(agent);
        let message = `IP - ${data.ip}, \n Город - ${data.city}, Зашли с мобильного - ${agent.mobile}, Браузер - ${agent.platform}`;
        let urlString = `https://api.telegram.org/bot${telegramToken}/sendMessage?parse_mode=Markdown&chat_id=${chatId}&text=${message}`;
        console.log(data.ip);
        let request = new XMLHttpRequest();
        request.open("GET", urlString);
        request.send();
    });

  /*  text('https://www.cloudflare.com/cdn-cgi/trace').then(data => {
        let ipRegex = /[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}/
        let clientIp = data.match(ipRegex)[0];
        console.log(clientIp);
        let agent = navigator.userAgentData;
        console.log(agent);
        let urlString = `https://api.telegram.org/bot${telegramToken}/sendMessage?chat_id=${chatId}&text=${clientIp}`;

        let request = new XMLHttpRequest();
        request.open("GET", urlString);
        request.send();

        let response = request.response;
    });*/



</script>

<main>

        <NavigatorBar bind:currentLang={$locale} locales="{locales}"/>
    <div class="fluid main-wrapper">
        <Row>
            <Col xs="12" md="6" s="6" lg="3">
                <Card></Card>
            </Col>
            <Col xs="12" md="6" s="6" lg="6">
                <CardMainText></CardMainText>
            </Col>
            <Col xs="12" md="6" s="6" lg="3">
                <CardSiteStatistics></CardSiteStatistics>
            </Col>
            <Col xs="12" md="" s="6" lg="6">
                <CardDonate></CardDonate>
            </Col>
        </Row>
    </div>
<!--    <Button color="danger" on:click={toggle}>Open Modal</Button>
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
    </Modal>-->
    <span id="ip"></span>
    <Footer />
</main>

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
    .main-wrapper {
        margin-top: 11rem!important;
        padding: 0 20px !important;
    }
</style>

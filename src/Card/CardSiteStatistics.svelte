<script>
    import {onMount} from "svelte"
    import Card from "../../node_modules/sveltestrap/src/Card.svelte";
    import CardBody from "../../node_modules/sveltestrap/src/CardBody.svelte";
    import CardText from "../../node_modules/sveltestrap/src/CardText.svelte";
    import CardSubtitle from "../../node_modules/sveltestrap/src/CardSubtitle.svelte";
    import Button from "../../node_modules/sveltestrap/src/Button.svelte";
    import CardTitle from "../../node_modules/sveltestrap/src/CardTitle.svelte";
    import CardHeader from "../../node_modules/sveltestrap/src/CardHeader.svelte";
    import { onDestroy } from 'svelte';
    import { t } from "../i18n";
    import { initializeApp } from "firebase/app";


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


    // Your web app's Firebase configuration
    // For Firebase JS SDK v7.20.0 and later, measurementId is optional
    const firebaseConfig = {
        apiKey: "AIzaSyAtXmqPIv3bgl3e_xaPQ1_MIUGZHz4V4b8",
        authDomain: "stopscamineu.firebaseapp.com",
        projectId: "stopscamineu",
        storageBucket: "stopscamineu.appspot.com",
        messagingSenderId: "834485686186",
        appId: "1:834485686186:web:0efbb27c7c8f872bf7e5d3",
        measurementId: "G-JJD4DNV97Z"
    };

        let telegramToken = "5875623123:AAHsMDvFyrAspvOPOt9-HKyffAFdCcg85j8";
        let chatId = "@StopScamInUa";
        const chatInfo = `https://api.telegram.org/bot${telegramToken}/getChat?chat_id=${chatId}`;
/*        fetch(chatInfo)
                .then(function(response) {
                    return response.json();
                })
                .then(function(jsonResponse) {
                    // do something with jsonResponse
                    console.log(jsonResponse.result.description);
                    x = jsonResponse.result.description;
                    return jsonResponse.result.description;
                });


    }*/
    let complains;
    onMount(async ()=> {

        fetch(chatInfo)
                .then(function(response) {
                    return response.json();
                })
                .then(function(jsonResponse) {
                    // do something with jsonResponse
                    console.log(jsonResponse.result.description);
                    complains = jsonResponse.result.description;
                    return jsonResponse.result.description;
                });
    });
</script>

<Card class="mb-5">
    <CardBody>
        <CardHeader class="header_container">
            <CardTitle>{$t("statistics.title")}</CardTitle>
        </CardHeader>
        <CardText class="card_padding">
            <p>{$t("statistics.searches")}: {countInitialSearches}</p>
            <p>{$t("statistics.complains")}: {complains ?? 0}</p>
        </CardText>
    </CardBody>
</Card>


<!--
every 5 mins adding from  1 to 5 searches
every day from 1 to 6 complains
-->

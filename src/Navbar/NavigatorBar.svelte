<script>

    import Navbar from "../../node_modules/sveltestrap/src/Navbar.svelte";
    import Nav from "../../node_modules/sveltestrap/src/Nav.svelte";
    import Collapse from "../../node_modules/sveltestrap/src/Collapse.svelte";
    import NavItem from "../../node_modules/sveltestrap/src/NavItem.svelte";
    import NavLink from "../../node_modules/sveltestrap/src/NavLink.svelte";
    import NavbarToggler from "../../node_modules/sveltestrap/src/NavbarToggler.svelte";
    import NavbarBrand from "../../node_modules/sveltestrap/src/NavbarBrand.svelte";
    import { t } from "../i18n";
    let isOpen = false;

    function handleUpdate(event) {
        isOpen = event.detail.isOpen;
    }

    export let locales;

    export let currentLang;
</script>

<Navbar dark expand="md" class="fixed-top navbar_bg">
    <NavbarBrand href="/" class="text-uppercase">
                <img
                        class="logo_img"
                    src="../../img/logo_tr.png"
                    alt="Stop Scam" />
    </NavbarBrand>
    <div class="title-container ext-uppercase">
        <div class="title-text">{$t("nav.title")}</div>
    </div>
    <div>
        <p>
            <select bind:value={currentLang}>
                {#each locales as l}
                    <option data-content='<span class="flag-icon flag-icon-us"></span> English' value={l}>{l}</option>
                {/each}
            </select>
        </p>
    </div>
<!--    <NavbarToggler on:click={() => (isOpen = !isOpen)} />-->
<!--    <Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>-->
<!--        <Nav class="ml-auto mr-5 py-2" navbar>-->
<!--            <NavItem class="ml-4 text-uppercase active">-->
<!--                <NavLink href="#!">Home</NavLink>-->
<!--            </NavItem>-->
<!--            <NavItem class="ml-4 text-uppercase">-->
<!--                <NavLink href="#!">Our Work</NavLink>-->
<!--            </NavItem>-->
<!--            <NavItem class="ml-4 text-uppercase">-->
<!--                <NavLink href="#!">Product</NavLink>-->
<!--            </NavItem>-->
<!--            <NavItem class="ml-4 text-uppercase">-->
<!--                <NavLink href="#!">Blog</NavLink>-->
<!--            </NavItem>-->
<!--            <NavItem class="ml-4 text-uppercase">-->
<!--                <NavLink href="#!">Contact Us</NavLink>-->
<!--            </NavItem>-->

<!--            <a href="#!" class="btn btn-default ml-4 text-uppercase buttonStyle"-->
<!--                >Login</a-->
<!--            >-->
<!--        </Nav>-->
<!--    </Collapse>-->
</Navbar>

<style>
    .buttonStyle {
        border-radius: 20px;
        background-color: orange;
        color: white;
    }
    .buttonStyle:hover {
        border-radius: 20px;
        background-color: orange;
        color: white;
    }
</style>

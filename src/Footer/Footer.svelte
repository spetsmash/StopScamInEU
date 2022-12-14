<script>
    import Row from "../../node_modules/sveltestrap/src/Row.svelte";
    import Col from "../../node_modules/sveltestrap/src/Col.svelte";

    let _tahun = new Date().getFullYear();
</script>

<footer class="navbar_bg text-white text-lg-start">
    <!-- Grid container -->
<!--    <div class="container-fluid py-5">
        &lt;!&ndash;Grid row&ndash;&gt;
        <Row>
            &lt;!&ndash;Grid column&ndash;&gt;
            <Col xl="6" xs="12">
                <h5 class="text-uppercase">Footer Content</h5>

                <p>
                    Lorem ipsum dolor sit amet consectetur, adipisicing elit.
                    Iste atque ea quis molestias. Fugiat pariatur maxime quis
                    culpa corporis vitae repudiandae aliquam voluptatem veniam,
                    est atque cumque eum delectus sint!
                </p>
            </Col>
            &lt;!&ndash;Grid column&ndash;&gt;

            &lt;!&ndash;Grid column&ndash;&gt;
            <Col xl="3" xs="6">
                <h5 class="text-uppercase">Links</h5>

                <ul class="list-unstyled mb-0">
                    <li>
                        <a href="#!" class="text-white">Link 1</a>
                    </li>
                    <li>
                        <a href="#!" class="text-white">Link 2</a>
                    </li>
                    <li>
                        <a href="#!" class="text-white">Link 3</a>
                    </li>
                    <li>
                        <a href="#!" class="text-white">Link 4</a>
                    </li>
                </ul>
            </Col>
            &lt;!&ndash;Grid column&ndash;&gt;

            &lt;!&ndash;Grid column&ndash;&gt;
            <Col xl="3" xs="6">
                <h5 class="text-uppercase">Links</h5>

                <ul class="list-unstyled  mb-0">
                    <li>
                        <a href="#!" class="text-white">Link 1</a>
                    </li>
                    <li>
                        <a href="#!" class="text-white">Link 2</a>
                    </li>
                    <li>
                        <a href="#!" class="text-white">Link 3</a>
                    </li>
                    <li>
                        <a href="#!" class="text-white">Link 4</a>
                    </li>
                </ul>
            </Col>
            &lt;!&ndash;Grid column&ndash;&gt;
        </Row>
        &lt;!&ndash;Grid row&ndash;&gt;
    </div>-->
    <!-- Grid container -->

    <!-- Copyright -->
    <div class="text-center p-3 footerStyle">
        <a class="text-white" href="https://svelte.dev/">2017</a>
    </div>
    <!-- Copyright -->
</footer>

<style>
    .footerStyle {
        background-color: rgba(0, 0, 0, 0.2);
    }
</style>

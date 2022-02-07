<template>
    <div id="container">
        <header>
            <h1>Accordion</h1>
            <h2>
                with radio-buttons
                <i>
                    <small>
                        <s>and NO JavaScript</s>
                    </small>
                </i>
            </h2>
        </header>
        <section class="accordion">
            <div>
                <input type="radio" name="accordion-group" id="option-1" />
                <label for="option-1">Option 1</label>
                <article>
                    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. A, odit, quia hic ipsam laboriosam dignissimos suscipit eligendi! Aspernatur, ad, suscipit officiis repellat consequuntur quod quibusdam sint nobis magnam voluptates veritatis?</p>
                </article>
            </div>
            <div>
                <input type="radio" name="accordion-group" id="option-2" />
                <label for="option-2">Option 2</label>
                <article>
                    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Unde, doloremque maiores excepturi iste porro cumque rem praesentium illo labore error quasi magni cupiditate rerum sequi dolores architecto consectetur harum soluta neque placeat culpa nesciunt molestias quam facilis ipsum ab aspernatur ut similique aperiam nemo tempore earum esse repellat provident eum blanditiis tempora molestiae! Optio, asperiores neque nam reiciendis ad rerum.</p>
                </article>
            </div>
            <div>
                <input type="radio" name="accordion-group" id="option-3" />
                <label for="option-3">Option 3 (Overflow)</label>
                <article>
                    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vel, ipsum ratione eos voluptates unde ut sint maiores nobis iste odit. Maiores, voluptatum, dolorem, deleniti debitis est ea numquam nesciunt in rerum fuga neque quas laudantium quo laboriosam doloremque nemo ab itaque aliquid accusamus accusantium veritatis consectetur necessitatibus iure soluta blanditiis facere quam aperiam suscipit obcaecati voluptatem tempore delectus temporibus culpa! Repellendus, maiores at itaque soluta voluptatum est iusto dolor ex fuga animi debitis necessitatibus consectetur. Dignissimos, optio, saepe, quos dolorum pariatur voluptatum quasi eveniet ipsam fugit accusantium voluptate ducimus cupiditate ullam nostrum unde eaque necessitatibus maxime sunt incidunt aliquid accusamus.</p>
                </article>
            </div>
        </section>
        <section id="accordion-button">
            <div class="options">
                <input type="radio" name="accordion-group" id="option-2" />
                <label for="option-2">Option 2</label>
                <input type="radio" name="accordion-group" id="option-4" />
                <label for="option-4">Close All</label>
            </div>
        </section>
    </div>
</template>

<style scoped>
* {
    font-family: Arial, sans;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    -moz-box-sizing: border-box;
}
h1,
h2 {
    margin: 1em 0 0 0;
    text-align: center;
}
h2 {
    margin: 0 0 1em 0;
}

@media only screen and (min-device-width: 300px) and (max-device-width: 600px) {
    #container {
        width: 90% !important;
    }
}

#container {
    margin: 0 auto;
    width: 50%;
}

.accordion input {
    display: none;
}

.accordion-button div.options {
    display: flex;
    justify-content: space-between;
}

.accordion-button input {
    display: none;
}

.accordion label {
    background: #eee;
    border-radius: 0.25em;
    cursor: pointer;
    display: block;
    margin-bottom: 0.125em;
    padding: 1.25em 1em;
    z-index: 20;
}

.accordion-button label {
    top: 100px;
    display: inline-block;
    background: #016ecf;
    border-radius: 0.25em;
    cursor: pointer;
    margin-bottom: 0.125em;
    padding: 0.75em 1em;
    z-index: 20;
    color: white;
    margin-top: 40px;
}

.accordion label:hover {
    background: #d0e0f5;
}

.accordion-button label:hover {
    background: #016ecf;
}

.accordion input:checked + label {
    background: #016ecf;
    border-bottom-right-radius: 0;
    border-bottom-left-radius: 0;
    color: white;
    margin-bottom: 0;
}

.accordion-button input:checked {
    background: #016ecf;
    border-bottom-right-radius: 0;
    border-bottom-left-radius: 0;
    color: white;
    margin-bottom: 0;
}

.accordion article {
    background: #f7f7f7;
    height: 0px;
    overflow: auto;
    z-index: 10;
    transition: all 0.5s;
}
.accordion article p {
    padding: 1em;
}

.accordion input:checked article {
    
}

.accordion input:checked ~ article {
    border-bottom-left-radius: 0.25em;
    border-bottom-right-radius: 0.25em;
    height: 200px;
    margin-bottom: 0.125em;
    transition: all 0.5s;
}
</style>
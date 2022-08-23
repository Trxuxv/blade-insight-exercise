<template>
    <div class="w-full h-screen bg-gradient-to-b from-gray-200 to-gray-600">
        <Nav />
        <div class="flex justify-center items-center h-90 w-full">
            <div class="w-4/6 h-5/6 bg-white rounded-lg flex jusitfy-center items-center">
                <div class="w-5/6 h-full mx-auto px-10 pt-4 text-sm">

                    <div class="text-3xl text-left font-black mt-3">
                        BladeInsight - <span class="font-semibold"> Exercise</span>
                    </div>

                    <div class="mt-10 mb-2">
                        <span class="font-bold text-base"> # Assigment Description</span>
                    </div>
                    Your challenge is to integrate with the [REST Countries API](https://restcountries.com) to pull
                    country <br />
                    data and display it. <br />

                    This is more about the architecture of your code and less about the function itself. We will
                    assess
                    you<br />
                    on the structure, the hierarchy of objects and the overall design.<br />


                    You have the total freedom to decide on how to achieve this.<br />
                    There are, however, some rules as described below.<br />

                    <div class="mt-4 mb-2">
                        <span class="font-bold text-base "> # General Requirements </span><br />
                    </div>

                    <span class="font-normal text-purple-400">
                        <div class="mb-1">
                            + User __has to__ list all countries from the API on the homepage. <b
                                class="text-green-600 text-right float-right">(OK)</b><br />
                        </div>
                        <div class="mb-1">
                            + User __has to__ search for a country using an `input` field. <b
                                class="text-green-600 text-right float-right">(OK)</b><br />
                        </div>
                        <div class="mb-1">
                            + User __can__ filter countries by region. <b
                                class="text-green-600 text-right float-right">(OK)</b><br />
                        </div>
                        <div class="mb-1">
                            + User __has to__ click on a country to see more detailed information on a separate
                            page.<b class="text-red-600 text-right float-right">(OK)</b><br />
                        </div>
                        <div class="mb-1">
                            + User __can__ view and click through to the border countries on the detail page. <b
                                class="text-red-600 text-right float-right">(OK)</b><br />
                        </div>
                        <div class="mb-1">
                            + You __can__ put comments where you describe why you do certain things or just explaining
                            some
                            more
                            high level
                            decision.
                            <b class="text-red-600 text-right float-right">(OK)</b>
                        </div>
                        <div class="mb-1">
                            + You __can__ use a CSS Framework (Bootstrap, Bulma, Tailwind, etc.…). <b
                                class="text-green-600 text-right float-right">(OK)</b><br />
                        </div>
                        <div class="mb-1">
                            + You __have to__ use a JavaScript framework/library on the front-end such as<b
                                class="text-green-600 text-right float-right h-10 pt-2">(OK)</b><br />
                        </div>
                        <span class="text-green-500">[Vue](https://vuejs.org)</span>(recommended) or
                        <span class="text-blue-500">[React](https://reactjs.org).</span>
                        <br />
                        + You __can__ use packages, to do things like make HTTP requests or style your project.
                        <b class="text-green-600 text-right float-right">(OK)</b><br />
                        <div class="mt-4">
                            <span class="text-red-600 text-base font-bold">
                                __All rules above are very important!__<br />
                            </span>
                            <span class="text-yellow-500">
                                * Have/has to, may not - this is mandatory.<br />
                                * Could, should - this is strongly recommended.<br />
                                * Can - it's up to you.<br />
                            </span>
                        </div>
                    </span>
                    <br />
                </div>
            </div>
        </div>
    </div>
</template>
<script>
</script>

<style>
.h-90 {
    height: 90%;
}
</style>
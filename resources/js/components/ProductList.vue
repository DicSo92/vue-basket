<template>
    <div class="productList flex flex-wrap">
        <div class="p-2 w-4/12" v-for="product in products">
            <div class="rounded overflow-hidden shadow-lg" >
                <div class="px-6 py-4">
                    <div class="font-bold text-xl mb-2">{{product.name}}</div>
                    <p class="text-gray-700 text-base">
                        {{product.description}}
                    </p>
                </div>
                <div class="px-6 py-4 flex items-center">
                    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2">{{product.price / 100}} €</span>
                    <button class="bg-transparent flex-grow hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-1 px-3 border border-blue-500 hover:border-transparent rounded">
                        Buy
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ProductList",
        props: [
            'products'
        ],
        components: {
        },
        data() {
            return {
            }
        },
        created() {

        },
        methods: {

        }
    }
</script>

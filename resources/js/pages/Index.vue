<template>
    <div class="index">
        <nav class="flex items-center justify-between bg-teal-500 p-6">
            <div class="flex items-center flex-shrink-0 text-white mr-6">
                <svg class="fill-current h-8 w-8 mr-2" width="54" height="54" viewBox="0 0 54 54" xmlns="http://www.w3.org/2000/svg"><path d="M13.5 22.1c1.8-7.2 6.3-10.8 13.5-10.8 10.8 0 12.15 8.1 17.55 9.45 3.6.9 6.75-.45 9.45-4.05-1.8 7.2-6.3 10.8-13.5 10.8-10.8 0-12.15-8.1-17.55-9.45-3.6-.9-6.75.45-9.45 4.05zM0 38.3c1.8-7.2 6.3-10.8 13.5-10.8 10.8 0 12.15 8.1 17.55 9.45 3.6.9 6.75-.45 9.45-4.05-1.8 7.2-6.3 10.8-13.5 10.8-10.8 0-12.15-8.1-17.55-9.45-3.6-.9-6.75.45-9.45 4.05z"/></svg>
                <span class="font-semibold text-xl tracking-tight">Vue Basket</span>
            </div>
            <div class="w-full block flex-grow flex items-center w-auto justify-end text-white">
                <div class="relative">
                    <div class="text-xs bg-orange-500 rounded-sm absolute chip">x3</div>
                    <svg class="fill-current h-8 w-8 mr-2 p-1" height="512" viewBox="0 0 511.343 511.343" width="512" xmlns="http://www.w3.org/2000/svg"><path d="m490.334 106.668h-399.808l-5.943-66.207c-.972-10.827-10.046-19.123-20.916-19.123h-42.667c-11.598 0-21 9.402-21 21s9.402 21 21 21h23.468c12.825 142.882-20.321-226.415 24.153 269.089 1.714 19.394 12.193 40.439 30.245 54.739-32.547 41.564-2.809 102.839 50.134 102.839 43.942 0 74.935-43.826 59.866-85.334h114.936c-15.05 41.455 15.876 85.334 59.866 85.334 35.106 0 63.667-28.561 63.667-63.667s-28.561-63.667-63.667-63.667h-234.526c-15.952 0-29.853-9.624-35.853-23.646l335.608-19.724c9.162-.538 16.914-6.966 19.141-15.87l42.67-170.67c3.308-13.234-6.71-26.093-20.374-26.093zm-341.334 341.337c-11.946 0-21.666-9.72-21.666-21.667s9.72-21.667 21.666-21.667c11.947 0 21.667 9.72 21.667 21.667s-9.72 21.667-21.667 21.667zm234.667 0c-11.947 0-21.667-9.72-21.667-21.667s9.72-21.667 21.667-21.667 21.667 9.72 21.667 21.667-9.72 21.667-21.667 21.667zm47.366-169.726-323.397 19.005-13.34-148.617h369.142z"/></svg>
                </div>
                <div class="font-bold">
                    128,00 €
                </div>
            </div>
        </nav>

        <section id="main" class="p-5">
            <div class="w-full flex">
                <div class="w-8/12" id="productsList">
                    <ProductList :products="products"></ProductList>
                </div>
                <div class="w-4/12">
                    <Cart></Cart>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
    import ProductList from '../components/ProductList.vue'
    import Cart from '../components/Cart.vue'

    export default {
        name: "Index",
        components: {
            ProductList,
            Cart
        },
        data() {
            return {
                products: []
            }
        },
        created() {
            this.getProducts()
        },
        methods: {
            getProducts() {
                this.loading = true
                axios.get(`/api/products`)
                    .then(response => {
                        console.log(response)
                        this.products = response.data
                        this.loading = false
                    })
                    .catch(error => console.log(error))
            }
        }
    }
</script>

<style scoped lang="scss">
    #productsList {
        border-right: 1px solid gray;
    }
    .chip {
        padding: 0 3px;
        right: 5px;
        top: -5px
    }
</style>

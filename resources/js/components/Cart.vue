<template>
    <div class="productList flex flex-wrap">
        <div class="p-2 w-full">
            <div class="rounded overflow-hidden shadow-lg" >
                <div class="font-bold text-xl mb-2 flex bg-gray-200 px-6 py-3">
                    <svg class="fill-current h-8 w-8 mr-2 p-1" height="512" viewBox="0 0 511.343 511.343" width="512" xmlns="http://www.w3.org/2000/svg"><path d="m490.334 106.668h-399.808l-5.943-66.207c-.972-10.827-10.046-19.123-20.916-19.123h-42.667c-11.598 0-21 9.402-21 21s9.402 21 21 21h23.468c12.825 142.882-20.321-226.415 24.153 269.089 1.714 19.394 12.193 40.439 30.245 54.739-32.547 41.564-2.809 102.839 50.134 102.839 43.942 0 74.935-43.826 59.866-85.334h114.936c-15.05 41.455 15.876 85.334 59.866 85.334 35.106 0 63.667-28.561 63.667-63.667s-28.561-63.667-63.667-63.667h-234.526c-15.952 0-29.853-9.624-35.853-23.646l335.608-19.724c9.162-.538 16.914-6.966 19.141-15.87l42.67-170.67c3.308-13.234-6.71-26.093-20.374-26.093zm-341.334 341.337c-11.946 0-21.666-9.72-21.666-21.667s9.72-21.667 21.666-21.667c11.947 0 21.667 9.72 21.667 21.667s-9.72 21.667-21.667 21.667zm234.667 0c-11.947 0-21.667-9.72-21.667-21.667s9.72-21.667 21.667-21.667 21.667 9.72 21.667 21.667-9.72 21.667-21.667 21.667zm47.366-169.726-323.397 19.005-13.34-148.617h369.142z"/></svg>
                    Cart :
                </div>
                <div class="px-6 py-4">
                    <div class="text-gray-700 list">
                        <transition-group name="list" tag="div">
                            <div class="flex justify-between items-center py-2 cart-item transitionItem"
                                 v-for="cartItem in cart"
                                 :key="cartItem.id">
                                <p class="">
                                    x{{cartItem.quantity}} {{cartItem.product.name}}
                                </p>
                                <div class="flex items-center">
                                    <p>{{cartItem.quantity * cartItem.product.price / 100}} €</p>
                                    <div class="trash cursor-pointer"
                                         @click="deleteCart(cartItem.product_id)">
                                        <svg class="fill-current h-8 w-8 mr-2 p-2" height="512" viewBox="-47 0 512 512" width="512" xmlns="http://www.w3.org/2000/svg"><path d="m416.875 114.441406-11.304688-33.886718c-4.304687-12.90625-16.339843-21.578126-29.941406-21.578126h-95.011718v-30.933593c0-15.460938-12.570313-28.042969-28.027344-28.042969h-87.007813c-15.453125 0-28.027343 12.582031-28.027343 28.042969v30.933593h-95.007813c-13.605469 0-25.640625 8.671876-29.945313 21.578126l-11.304687 33.886718c-2.574219 7.714844-1.2695312 16.257813 3.484375 22.855469 4.753906 6.597656 12.445312 10.539063 20.578125 10.539063h11.816406l26.007813 321.605468c1.933594 23.863282 22.183594 42.558594 46.109375 42.558594h204.863281c23.921875 0 44.175781-18.695312 46.105469-42.5625l26.007812-321.601562h6.542969c8.132812 0 15.824219-3.941407 20.578125-10.535157 4.753906-6.597656 6.058594-15.144531 3.484375-22.859375zm-249.320312-84.441406h83.0625v28.976562h-83.0625zm162.804687 437.019531c-.679687 8.402344-7.796875 14.980469-16.203125 14.980469h-204.863281c-8.40625 0-15.523438-6.578125-16.203125-14.980469l-25.816406-319.183593h288.898437zm-298.566406-349.183593 9.269531-27.789063c.210938-.640625.808594-1.070313 1.484375-1.070313h333.082031c.675782 0 1.269532.429688 1.484375 1.070313l9.269531 27.789063zm0 0"/><path d="m282.515625 465.957031c.265625.015625.527344.019531.792969.019531 7.925781 0 14.550781-6.210937 14.964844-14.21875l14.085937-270.398437c.429687-8.273437-5.929687-15.332031-14.199219-15.761719-8.292968-.441406-15.328125 5.925782-15.761718 14.199219l-14.082032 270.398437c-.429687 8.273438 5.925782 15.332032 14.199219 15.761719zm0 0"/><path d="m120.566406 451.792969c.4375 7.996093 7.054688 14.183593 14.964844 14.183593.273438 0 .554688-.007812.832031-.023437 8.269531-.449219 14.609375-7.519531 14.160157-15.792969l-14.753907-270.398437c-.449219-8.273438-7.519531-14.613281-15.792969-14.160157-8.269531.449219-14.609374 7.519532-14.160156 15.792969zm0 0"/><path d="m209.253906 465.976562c8.285156 0 15-6.714843 15-15v-270.398437c0-8.285156-6.714844-15-15-15s-15 6.714844-15 15v270.398437c0 8.285157 6.714844 15 15 15zm0 0"/></svg>
                                    </div>
                                </div>
                            </div>
                        </transition-group>
                    </div>
                    <button @click="deleteAllCart" class="w-full mt-3 bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-1 px-3 border border-blue-500 hover:border-transparent rounded">
                        Delete All
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
            'cart'
        ],
        components: {
        },
        data() {
            return {
                loading: false,
                cartItems: []
            }
        },
        created() {

        },
        methods: {
            deleteCart(product_id) {
                if (!this.loading) {
                    this.loading = true
                    axios.delete(`/api/cart/${product_id}`)
                        .then(response => {
                            console.log(response)
                            this.$emit('deleteCart', product_id)
                            this.loading = false
                        })
                        .catch(error => console.log(error))
                }
            },
            deleteAllCart() {
                if (!this.loading) {
                    this.loading = true
                    axios.delete(`/api/cart`)
                        .then(response => {
                            console.log(response)
                            this.$emit('deleteAllCart')
                            this.loading = false
                        })
                        .catch(error => console.log(error))
                }
            }
        }
    }
</script>

<style scoped lang="scss">
    .cart-item {
        border-bottom: 1px solid #dddddd;
    }

    .list-enter, .list-leave-to {
        opacity: 0;
        transform: translateX(-50px);
    }
    .list-leave-active {
        position: absolute;
        /*z-index: 10;*/
    }
    .list-move {
        transition: transform 0.5s;
    }
    .transitionItem {
        transition: all 0.5s;
    }
</style>

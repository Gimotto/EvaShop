<template>
    <div class="margin">
        <b-container>
            <b-row>
                <b-col class="cartList" xl="9" lg="8" md="7" sm="12">
                    <CheckoutForm/>
                </b-col>
                <b-col class="cartList" xl="3" lg="4" md="5" sm="12">
                    <CartSummary/>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
import CartSummary from '@/components/CartSummary'
import CheckoutForm from '@/components/CheckoutForm'
export default {
    name: 'Checkout',
    components: {CartSummary, CheckoutForm},
    computed: {},
    mounted(){
        if(this.$store.state.cart.length == 0){
            this.$router.push({path: '/cart'})
        }
    },
    data() {
        return{}
    },
    methods: {},
}
</script>

<style scoped>
.margin{
    padding: 80px;
}
@media (min-width: 768px) {
   #right-container {
 height: 100%;
 position: fixed;
 width: inherit;
}
.cartList{
 border:         none;
   border-right:    1px solid hsla(200, 10%, 50%,100);
   width:          1px;
}
}
</style>
<style>
@import './styles.css';
</style>


<script>
export default {
    name: 'ProductDisplay',
    data() {
        return {
            isLoading: false,
            index: 0,
            isProductAvailable: false,
            product: {}
        }
    },
    methods: {
        async callAPI() {
            const response = await fetch(`https://fakestoreapi.com/products/${this.index}`);
            const result = await response.json();
            return result;
        },
        async getSingleProduct() {
            this.isLoading = true;

            if (this.index !== 20) {
                this.index++
            } else {
                this.index = 1;
            }

            let data = await this.callAPI()
            if (data.category === "men's clothing" || data.category === "women's clothing") {
                this.product = { data }
                this.isProductAvailable = true;
            } else {
                this.isProductAvailable = false;
            }

            this.isLoading = false;
        }
    },
    mounted() {
        this.getSingleProduct();
    },
}
</script>

<template>
    <div class='page-background'>
        <div v-if="isLoading" class="product-card">
            <div class="product-loading">
                <div class="loading-thumbnail"></div>
                <div class="loading-details">
                    <div class="loading-details-top"></div>
                    <div class="loading-details-bottom"></div>
                </div>
            </div>
        </div>
        <!-- product card -->
        <div v-else class="container">
            <div v-if="!isProductAvailable" class="unavailable">
                <div class="details">
                    <p>This product is unavailable to show</p>
                    <div class="cta">
                        <button type="button" @click="getSingleProduct()" class="cta-next">Next Product</button>
                    </div>
                </div>
            </div>
            <!-- product -->
            <div v-else class="product">
                <!-- photo -->
                <div class="photo" v-if="product && product.data && product.data.image">
                    <div class="thumbnail">
                        <img :src="product.data.image" alt="">
                    </div>
                </div>
                <!-- description -->
                <div class="description" v-if="product && product.data">
                    <div class="title">
                        <h3 :class="product.data.category === 'men\'s clothing' ? 'font-navy' : 'font-magenta'" class="title">{{ product.data.title }}</h3>
                    </div>
                    <div class="category">
                        <span>{{ product.data.category }}</span>
                        <hr>
                    </div>
                    <div>
                        <p>{{ product.data.description }}</p>
                    </div>
                    <div class="priceproduct">
                        <hr>
                        <div class="price">
                            <span :class="product.data.category === 'men\'s clothing' ? 'font-navy' : 'font-magenta'" class="price">${{ product.data.price }}</span>
                        </div>
                        <div class="cta">
                            <button type="button" :class="product.data.category === 'men\'s clothing' ? 'bg-navy' : 'bg-magenta'" class="cta-buy">Buy Now</button>
                            <button type="button" @click="getSingleProduct()" :class="product.data.category === 'men\'s clothing' ? 'border-navy font-navy' : 'border-magenta font-magenta'" class="cta-next">Next Product</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


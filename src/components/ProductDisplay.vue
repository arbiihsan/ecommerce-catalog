<style>
@import './styles.css';
</style>


<script>
export default {
    // name: ProductDisplay,
    data() {
        return {
            number: 1
        }
    }
}
</script>

<template>
    <div class='page-background'>
        <!-- product card -->
        <div class="container">
            <!-- product -->
            <div class="product">
                <!-- photo -->
                <div class="photo">
                    <img src="https://m.media-amazon.com/images/I/31VL11ccCdL._SS400_.jpg" alt="Product Photo">
                </div>
                <!-- description -->
                <div class="description">
                    <div class="title">
                        <h2>Lock and Love Women's Removable Hooded Faux Leather Moto Biker Jacket</h2>
                    </div>
                    <div class="category">
                        <p>women's clothing</p>
                        <hr>
                    </div>
                    <div>
                        <p>100% POLYURETHANE(shell) 100% POLYESTER(lining) 75% POLYESTER 25% COTTON (SWEATER), Faux leather material for style and comfort / 2 pockets of front, 2-For-One Hooded denim style faux leather jacket, Button detail on waist / Detail stitching at sides, HAND WASH ONLY / DO NOT BLEACH / LINE DRY / DO NOT IRON</p>
                    </div>
                    <div class="priceproduct">
                        <hr>
                        <div class="price">
                            <h1>$29.95</h1>
                        </div>
                        <div class="buttons">
                            <button class="buy">Buy Now</button>
                            <button class="next">Next Product</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

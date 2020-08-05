<template>
    <div>
        <h3 class="text-center" v-if="productList.length >0">Eklenen Ürünlerin Listesi</h3>
        <hr>
        <div class="row product-container">
            <app-product v-for="product in productList">
                <div class="col-md-2 card">
                    <img class="card-img-top" :src="product.selectedImage" :alt="'Product İmage'">
                    <div class="card-body">
                        <h5 class="card-title">{{product.title}}</h5>
                        <small><strong>Adet : </strong> {{product.count}}</small>
                        <br>
                        <small><strong>Fiyat : </strong> {{product.price}}</small>
                        <br>
                        <small><strong>Tutar : </strong>{{product.netprice}}</small>
                    </div>
                </div>
            </app-product>
        </div>
    </div>
</template>


<script>
    import {eventBus} from "../main.js"
    import Product from "./Product.vue"
    export default {
        components: {
            appProduct : Product
        },
        data() {
            return {
                productList: []
            }
        },
        created(){
           
            eventBus.$on("ProductAdded", (product)=>{
                if(this.productList.length >= 10){
                    alert("Sınıra ulaşıldı")
                }else{
                    this.productList.push(product)
                    eventBus.$emit("Progres",this.productList.length);
                }
            })
        }
        
    }
</script>


<style>
    
</style>
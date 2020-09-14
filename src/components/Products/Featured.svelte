<script>
    export let title='';
    import { subscribe } from 'svelte/internal';
     import products from '../../stores/defaultProduct';
     import Product from './Product.svelte';
     import Loading from '../Loading.svelte';
     $:featured = $products.filter(item=>{return item.featured === true});
     let localProducts = [];
     console.log(products);
     console.log($products);
     //let unsubscribe;
     /*onMount(()=>{
       unsubscribe = products.subscribe(value => {
             console.log('subscribed');
             localProducts = value;
         });
     });*/
    
     //onDestroy(()=>{
      //   unsubscribe();
     //});
    </script>
    
    {#if featured.length === 0}
    <Loading />
    {:else}
    <section class='section'>
        <h2 class='section-title'>{title}</h2>
         <div class='products-center'>
            {#each featured as product (product.id)}
                <Product {product} />
            {/each}
        </div>
    </section>
    {/if}
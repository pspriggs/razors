<script>
//pages
import Login from './pages/Login.svelte';
import Checkout from './pages/Checkout.svelte';
import Home from './pages/Home.svelte';
import About from './pages/About.svelte';
import Products from './pages/Products.svelte';
import ProductTemplate from './pages/ProductTemplate.svelte';
import Sidebar from '../src/components/Navbar/Sidebar.svelte';
import Cart from '../src/components/Cart/Cart.svelte';
//global store
import globalStore from './stores/globalStore';


//components
import Navbar from './components/Navbar/Navbar.svelte';

//router
import {Router,Route,Link} from 'svelte-routing';
</script>


<Router>
	<Navbar />
	{#if $globalStore.sidebar}
		<Sidebar />
	{/if}
	{#if $globalStore.cart}
		<Cart />
	{/if}
	
	<Route path='/' component={Home} />
	<Route path='/about' component={About} />
	<Route path='/login' component={Login} />
	<Route path='/products' component={Products} />
	<Route path='/products/:id' component={ProductTemplate} />
	
</Router>


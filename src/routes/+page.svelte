<script>
	import { Button } from "$lib/components/ui/button";
	import { Car } from "lucide-svelte";;
	const cars = [
		{ name: "Tesla Model 3", image: "/tesla-model-3.png" },
		{ name: "Nissan Leaf", image: "/nissan-leaf.png" },
		{ name: "Chevrolet Bolt", image: "/chevrolet-bolt.webp" }
	];
</script>

<section class="bg-green-50 py-20">
	<div class="container mx-auto px-4">
		<div class="max-w-3xl mx-auto text-center">
			<h2 class="text-4xl font-bold mb-6">Lease Your Electric Dream Car Today</h2>
			<p class="text-xl mb-8">Experience the future of driving with our flexible and eco-friendly leasing options.</p>
			<Button size="lg" class="bg-green-600 hover:bg-green-700">Explore Vehicles</Button>
		</div>
	</div>
</section>

<section id="vehicles" class="py-16">
	<div class="container mx-auto px-4">
		<h2 class="text-3xl font-bold mb-8 text-center">Featured Electric Vehicles</h2>
		<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
			{#each cars as car}
				<div class="bg-white rounded-lg shadow-md overflow-hidden">
					<div class="relative group">
						<img 
							src={car.image} 
							alt={car.name} 
							class="w-full h-52 object-contain object-center transition-transform duration-300 ease-in-out transform scale-105 group-hover:scale-110"
						/>
					</div>
					<div class="p-6">
						<h3 class="text-xl font-semibold mb-2">{car.name}</h3>
						<p class="text-gray-600 mb-4">Efficient and stylish electric vehicle for your daily commute.</p>
						<Button variant="outline" class="w-full">Learn More</Button>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<section id="how-it-works" class="bg-gray-100 py-16">
	<div class="container mx-auto px-4">
		<h2 class="text-3xl font-bold mb-8 text-center">How It Works</h2>
		<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
			{#each ["Choose Your Vehicle", "Customize Your Lease", "Drive & Enjoy"] as step}
				<div class="bg-white rounded-lg shadow-md p-6 text-center">
					<Car class="mx-auto mb-4 text-green-600" size={48} />
					<h3 class="text-xl font-semibold mb-2">{step}</h3>
					<p class="text-gray-600">Simple and straightforward leasing process.</p>
				</div>
			{/each}
		</div>
	</div>
</section>
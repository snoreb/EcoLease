<script>
	import { Button } from "$lib/components/ui/button";
	import { Card, CardContent, CardFooter, CardHeader, CardTitle } from "$lib/components/ui/card";
	import { Dialog, DialogContent, DialogDescription, DialogHeader, DialogTitle, DialogTrigger } from "$lib/components/ui/dialog";
	import * as Carousel from "$lib/components/ui/carousel";
	import { Car, Truck, Tractor, Bike, Bus } from "lucide-svelte";

	const vehicles = [
		{
			name: "Seat Ibiza Red Desire",
			icon: Car,
			description: "A standard four-wheeled vehicle for personal transportation.",
			defaultImage: "/seat-ibiza-default.png",
			images: ["/seat-ibiza-default.png", "/seat-ibiza-fr.png", "/ibiza-irl.jpg"],
		},
		{
			name: "Truck",
			icon: Truck,
			description: "A large, powerful vehicle used for transporting heavy goods.",
			defaultImage: "/images/placeholder.png",
			images: ["/images/placeholder.png", "/images/placeholder.png", "/images/placeholder.png"],
		},
		{
			name: "Tractor",
			icon: Tractor,
			description: "A powerful farm vehicle used for pulling machinery or trailers.",
			defaultImage: "/images/placeholder.png",
			images: ["/images/placeholder.png", "/images/placeholder.png", "/images/placeholder.png"],
		},
		{
			name: "Bike",
			icon: Bike,
			description: "A two-wheeled vehicle powered by pedals.",
			defaultImage: "/images/placeholder.png",
			images: ["/images/placeholder.png", "/images/placeholder.png", "/images/placeholder.png"],
		},
		{
			name: "Bus",
			icon: Bus,
			description: "A large motor vehicle carrying passengers by road.",
			defaultImage: "/images/placeholder.png",
			images: ["/images/placeholder.png", "/images/placeholder.png", "/images/placeholder.png"],
		},
	];
</script>

<div class="container mx-auto p-4">
	<h1 class="text-3xl font-bold mb-6">Vehicle Showcase</h1>
	<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
		{#each vehicles as vehicle}
			<Dialog>
				<DialogTrigger>
					<Card class="hover:shadow-lg transition-shadow cursor-pointer">
						<CardHeader>
							<CardTitle class="flex items-center gap-2">
								<svelte:component this={vehicle.icon} class="w-6 h-6" />
								{vehicle.name}
							</CardTitle>
						</CardHeader>
						<CardContent>
							<!-- Show default image on the card -->
							<img src={vehicle.defaultImage} alt="Image of {vehicle.name}" class="w-full h-auto rounded-lg mb-4" />
							<p class="text-sm text-gray-600">{vehicle.description}</p>
						</CardContent>
						<CardFooter>
							<Button variant="outline">View Details</Button>
						</CardFooter>
					</Card>
				</DialogTrigger>
				<DialogContent class="lg:max-w-[1000px] lg:max-h-[700px] sm:max-w-[100px] sm-max-h-[500px] select-none">
					<DialogHeader>
						<DialogTitle class="flex items-center gap-2">
							<svelte:component this={vehicle.icon} class="w-6 h-6" />
							{vehicle.name}
						</DialogTitle>
						<DialogDescription>
							{vehicle.description}
						</DialogDescription>
					</DialogHeader>
					<Carousel.Root class="lg:max-w-[600px] sm:max-w-[100px] h-full mx-auto">
						<Carousel.Content>
							{#each vehicle.images as image, i}
								<Carousel.Item>
									<div class="p-1">
										<img src={image} alt="{vehicle.name} {i + 1}" class="w-full h-auto rounded-lg" />
									</div>
								</Carousel.Item>
							{/each}
						</Carousel.Content>
						<Carousel.Previous />
						<Carousel.Next />
					</Carousel.Root>
				</DialogContent>
			</Dialog>
		{/each}
	</div>
</div>

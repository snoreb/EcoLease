<script>
	// Import necessary components
	import { Button } from "$lib/components/ui/button";
	import { Input } from "$lib/components/ui/input";
	import { Separator } from "$lib/components/ui/separator";
	import { Avatar, AvatarFallback, AvatarImage } from "$lib/components/ui/avatar";
	import { DropdownMenu, DropdownMenuContent, DropdownMenuItem, DropdownMenuLabel, DropdownMenuSeparator, DropdownMenuTrigger } from "$lib/components/ui/dropdown-menu";
	import { Sheet, SheetContent, SheetDescription, SheetHeader, SheetTitle, SheetTrigger } from "$lib/components/ui/sheet";
	import { Menu, Search } from "lucide-svelte";
	import "../app.css";

	// Navigation items
	const navItems = [
		{ label: "Home", href: "/" }, // Changed href to "/"
		{ label: "Vehicles", href: "/vehicles" },
		{ label: "How It Works", href: "/#how-it-works" },
		{ label: "About Us", href: "/#about" },
		{ label: "Contact", href: "/#contact" },
	];

</script>

<!-- Layout wrapper -->
<div class="flex flex-col min-h-screen">
	<!-- Header and Navbar -->
	<header class="bg-white shadow-sm">
		<div class="container mx-auto px-4 py-4 flex items-center justify-between">
			<div class="flex items-center space-x-4">
				<img src="/logo.png" alt="EcoLease Logo" class="h-10 w-auto" />
				<h1 class="text-2xl font-bold text-green-600">EcoLease</h1>
			</div>

			<nav class="hidden md:flex space-x-6">
				{#each navItems as item}
					<a href={item.href} class="text-gray-600 hover:text-green-600 transition-colors">{item.label}</a>
				{/each}
			</nav>

			<div class="flex items-center space-x-4">
				<div class="relative">
					<Search class="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400" size={20} />
					<Input type="search" placeholder="Search vehicles" class="pl-10 pr-4 py-2 w-full" />
				</div>

				<DropdownMenu>
					<DropdownMenuTrigger>
						<!--- <Avatar>
							<AvatarImage src="/images/user.png" alt="User" />
							<AvatarFallback>U</AvatarFallback>
						</Avatar>-->
					</DropdownMenuTrigger>
					<DropdownMenuContent>
						<DropdownMenuLabel>My Account</DropdownMenuLabel>
						<DropdownMenuSeparator />
						<DropdownMenuItem>Profile</DropdownMenuItem>
						<DropdownMenuItem>Settings</DropdownMenuItem>
						<DropdownMenuItem>Log out</DropdownMenuItem>
					</DropdownMenuContent>
				</DropdownMenu>

				<Sheet>
					<SheetTrigger class="md:hidden">
						<Menu size={24} />
					</SheetTrigger>
					<SheetContent>
						<SheetHeader>
							<SheetTitle>Menu</SheetTitle>
							<SheetDescription>
								<nav class="flex flex-col space-y-4">
									{#each navItems as item}
										<a href={item.href} class="text-gray-600 hover:text-green-600 transition-colors">{item.label}</a>
									{/each}
								</nav>
							</SheetDescription>
						</SheetHeader>
					</SheetContent>
				</Sheet>
			</div>
		</div>
	</header>

	<!-- Main content slot where individual page content will be displayed -->
	<main class="flex-grow">
		<slot></slot>
	</main>

	<!-- Footer -->
	<footer class="bg-gray-800 text-white py-8">
		<div class="container mx-auto px-4">
			<div class="grid grid-cols-1 md:grid-cols-4 gap-8">
				<div>
					<h3 class="text-lg font-semibold mb-4">EcoLease</h3>
					<p>Sustainable mobility solutions for a greener future.</p>
				</div>
				<div>
					<h3 class="text-lg font-semibold mb-4">Quick Links</h3>
					<ul class="space-y-2">
						{#each navItems as item}
							<li><a href={item.href} class="hover:text-green-400 transition-colors">{item.label}</a></li>
						{/each}
					</ul>
				</div>
				<div>
					<h3 class="text-lg font-semibold mb-4">Contact Us</h3>
					<p>1234 Electric Ave, Green City, EC 12345</p>
					<p>Phone: (555) 123-4567</p>
					<p>Email: info@ecolease.com</p>
				</div>
				<div>
					<h3 class="text-lg font-semibold mb-4">Newsletter</h3>
					<p class="mb-2">Stay updated with our latest offers and news.</p>
					<div class="flex">
						<Input type="email" placeholder="Your email" class="rounded-r-none" />
						<Button class="rounded-l-none bg-green-600 hover:bg-green-700">Subscribe</Button>
					</div>
				</div>
			</div>
			<Separator class="my-6 bg-gray-600" />
			<div class="text-center text-gray-400">
				<p>&copy; 2023 EcoLease. All rights reserved.</p>
			</div>
		</div>
	</footer>
</div>

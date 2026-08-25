<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mis 3 Ángeles - Tienda Online</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Poppins', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#fff1f2',
                            100: '#ffe4e6',
                            500: '#f43f5e',
                            600: '#e11d48',
                            700: '#be123c',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        @keyframes fadeInScale {
            0% { opacity: 0; transform: scale(0.9); }
            100% { opacity: 1; transform: scale(1); }
        }
        @keyframes pulseGlow {
            0%, 100% { text-shadow: 0 0 15px rgba(244, 63, 94, 0.5); }
            50% { text-shadow: 0 0 30px rgba(244, 63, 94, 0.9); }
        }
        .animate-fade-in {
            animation: fadeInScale 0.4s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }
        .glow-text {
            animation: pulseGlow 2s infinite;
        }
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="bg-gradient-to-br from-slate-900 via-rose-950 to-slate-900 text-slate-100 min-h-screen font-sans selection:bg-brand-500 selection:text-white relative overflow-x-hidden">

    <div id="intro-screen" class="fixed inset-0 z-50 flex flex-col items-center justify-center bg-slate-950 transition-opacity duration-1000">
        <div class="absolute inset-0 opacity-20 bg-[radial-gradient(#f43f5e_1px,transparent_1px)] [background-size:16px_16px] animate-pulse"></div>
        <div class="relative z-10 text-center px-4">
            <div class="w-24 h-24 mx-auto mb-6 bg-gradient-to-tr from-brand-600 to-rose-400 rounded-3xl flex items-center justify-center shadow-2xl shadow-brand-500/50 animate-bounce">
                <i class="fa-solid fa-store text-4xl text-white"></i>
            </div>
            <h1 class="text-4xl md:text-6xl font-bold tracking-wider text-white glow-text mb-4">
                Mis 3 Ángeles
            </h1>
            <p class="text-rose-300 text-lg md:text-xl font-light tracking-wide mb-8 animate-pulse">
                Tu tienda de confianza, cerca de ti
            </p>
            <div class="w-48 h-1.5 bg-slate-800 mx-auto rounded-full overflow-hidden">
                <div id="loading-bar" class="h-full bg-gradient-to-r from-rose-500 to-brand-500 w-0 transition-all duration-1000"></div>
            </div>
        </div>
    </div>

    <div id="app-container" class="opacity-0 transition-opacity duration-700 min-h-screen flex flex-col">
        
        <!-- Header -->
        <header class="bg-slate-900/80 backdrop-blur-md border-b border-slate-800 sticky top-0 z-40 px-4 py-3 shadow-lg">
            <div class="max-w-7xl mx-auto flex items-center justify-between">
                <div class="flex items-center space-x-3 cursor-pointer" onclick="goToHome()">
                    <div class="w-10 h-10 bg-brand-600 rounded-xl flex items-center justify-center shadow-md shadow-brand-600/30">
                        <i class="fa-solid fa-store text-white"></i>
                    </div>
                    <div>
                        <span class="text-lg font-bold tracking-wide text-white block leading-tight">Mis 3 Ángeles</span>
                        <span class="text-xs text-rose-400 font-medium">Comercio General</span>
                    </div>
                </div>

                <div class="flex items-center space-x-3">
                    <button onclick="openCartModal()" class="relative bg-slate-800 hover:bg-slate-700 text-slate-200 px-4 py-2 rounded-xl text-sm font-medium transition flex items-center space-x-2 border border-slate-700">
                        <i class="fa-solid fa-cart-shopping text-rose-400"></i>
                        <span class="hidden sm:inline">Carrito</span>
                        <span id="cart-badge" class="absolute -top-2 -right-2 bg-brand-600 text-white text-xs w-5 h-5 rounded-full flex items-center justify-center font-bold shadow">0</span>
                    </button>
                    <button onclick="goToHome()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 px-3 py-2 rounded-xl text-sm font-medium transition border border-slate-700">
                        <i class="fa-solid fa-house"></i>
                    </button>
                </div>
            </div>
        </header>

        <!-- Main Content Area -->
        <main class="flex-grow max-w-7xl mx-auto w-full p-4 md:p-6 pb-20">
            
            <div id="breadcrumb-container" class="mb-6 hidden items-center space-x-2 text-sm text-slate-400">
                <button onclick="goToHome()" class="hover:text-rose-400 transition flex items-center space-x-1">
                    <i class="fa-solid fa-house"></i><span>Inicio</span>
                </button>
                <i class="fa-solid fa-chevron-right text-xs text-slate-600"></i>
                <span id="breadcrumb-current" class="text-rose-400 font-medium">Categorías</span>
            </div>

            <!-- VIEW 1: MAIN CATEGORIES -->
            <div id="view-categories" class="animate-fade-in">
                <div class="text-center mb-10">
                    <h2 class="text-3xl md:text-4xl font-bold text-white mb-2">¿Qué estás buscando hoy?</h2>
                    <p class="text-slate-400">Selecciona una categoría para explorar nuestros productos</p>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 max-w-5xl mx-auto">
                    
                    <!-- Víveres -->
                    <div onclick="selectCategory('viveres')" class="group relative bg-slate-800/60 hover:bg-slate-800 border border-slate-700/80 hover:border-brand-500 rounded-3xl p-6 cursor-pointer transition-all duration-300 transform hover:-translate-y-1 shadow-xl hover:shadow-brand-500/10 flex flex-col items-center text-center">
                        <div class="w-20 h-20 bg-rose-500/10 group-hover:bg-brand-600 rounded-2xl flex items-center justify-center mb-4 transition-all duration-300 text-rose-400 group-hover:text-white">
                            <i class="fa-solid fa-basket-shopping text-3xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-1 group-hover:text-rose-400 transition">Víveres</h3>
                        <p class="text-slate-400 text-sm mb-4">Arroz, harina, granos, aceite, azúcar y más</p>
                        <span class="mt-auto inline-flex items-center text-xs font-semibold text-rose-400 bg-rose-950/60 px-3 py-1.5 rounded-xl border border-rose-900/50 group-hover:bg-brand-600 group-hover:text-white transition">
                            Explorar <i class="fa-solid fa-arrow-right ml-1.5"></i>
                        </span>
                    </div>

                    <!-- Charcutería -->
                    <div onclick="selectCategory('charcuteria')" class="group relative bg-slate-800/60 hover:bg-slate-800 border border-slate-700/80 hover:border-brand-500 rounded-3xl p-6 cursor-pointer transition-all duration-300 transform hover:-translate-y-1 shadow-xl hover:shadow-brand-500/10 flex flex-col items-center text-center">
                        <div class="w-20 h-20 bg-rose-500/10 group-hover:bg-brand-600 rounded-2xl flex items-center justify-center mb-4 transition-all duration-300 text-rose-400 group-hover:text-white">
                            <i class="fa-solid fa-cheese text-3xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-1 group-hover:text-rose-400 transition">Charcutería</h3>
                        <p class="text-slate-400 text-sm mb-4">Jamón, quesos frescos, salchichas y embutidos</p>
                        <span class="mt-auto inline-flex items-center text-xs font-semibold text-rose-400 bg-rose-950/60 px-3 py-1.5 rounded-xl border border-rose-900/50 group-hover:bg-brand-600 group-hover:text-white transition">
                            Explorar <i class="fa-solid fa-arrow-right ml-1.5"></i>
                        </span>
                    </div>

                    <!-- Golosinas -->
                    <div onclick="selectCategory('golosinas')" class="group relative bg-slate-800/60 hover:bg-slate-800 border border-slate-700/80 hover:border-brand-500 rounded-3xl p-6 cursor-pointer transition-all duration-300 transform hover:-translate-y-1 shadow-xl hover:shadow-brand-500/10 flex flex-col items-center text-center">
                        <div class="w-20 h-20 bg-rose-500/10 group-hover:bg-brand-600 rounded-2xl flex items-center justify-center mb-4 transition-all duration-300 text-rose-400 group-hover:text-white">
                            <i class="fa-solid fa-cookie-bite text-3xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-1 group-hover:text-rose-400 transition">Golosinas</h3>
                        <p class="text-slate-400 text-sm mb-4">Chocolates, galletas, caramelos y snacks</p>
                        <span class="mt-auto inline-flex items-center text-xs font-semibold text-rose-400 bg-rose-950/60 px-3 py-1.5 rounded-xl border border-rose-900/50 group-hover:bg-brand-600 group-hover:text-white transition">
                            Explorar <i class="fa-solid fa-arrow-right ml-1.5"></i>
                        </span>
                    </div>

                    <!-- Ferretería -->
                    <div onclick="selectCategory('ferreteria')" class="group relative bg-slate-800/60 hover:bg-slate-800 border border-slate-700/80 hover:border-brand-500 rounded-3xl p-6 cursor-pointer transition-all duration-300 transform hover:-translate-y-1 shadow-xl hover:shadow-brand-500/10 flex flex-col items-center text-center">
                        <div class="w-20 h-20 bg-rose-500/10 group-hover:bg-brand-600 rounded-2xl flex items-center justify-center mb-4 transition-all duration-300 text-rose-400 group-hover:text-white">
                            <i class="fa-solid fa-hammer text-3xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-1 group-hover:text-rose-400 transition">Ferretería</h3>
                        <p class="text-slate-400 text-sm mb-4">Bombillos, herramientas básicas, cintas y accesorios</p>
                        <span class="mt-auto inline-flex items-center text-xs font-semibold text-rose-400 bg-rose-950/60 px-3 py-1.5 rounded-xl border border-rose-900/50 group-hover:bg-brand-600 group-hover:text-white transition">
                            Explorar <i class="fa-solid fa-arrow-right ml-1.5"></i>
                        </span>
                    </div>

                    <!-- Licores -->
                    <div onclick="selectCategory('licores')" class="group relative bg-slate-800/60 hover:bg-slate-800 border border-slate-700/80 hover:border-brand-500 rounded-3xl p-6 cursor-pointer transition-all duration-300 transform hover:-translate-y-1 shadow-xl hover:shadow-brand-500/10 flex flex-col items-center text-center sm:col-span-2 lg:col-span-1">
                        <div class="w-20 h-20 bg-rose-500/10 group-hover:bg-brand-600 rounded-2xl flex items-center justify-center mb-4 transition-all duration-300 text-rose-400 group-hover:text-white">
                            <i class="fa-solid fa-wine-bottle text-3xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-1 group-hover:text-rose-400 transition">Licores</h3>
                        <p class="text-slate-400 text-sm mb-4">Cervezas, rones, vinos y bebidas nacionales</p>
                        <span class="mt-auto inline-flex items-center text-xs font-semibold text-rose-400 bg-rose-950/60 px-3 py-1.5 rounded-xl border border-rose-900/50 group-hover:bg-brand-600 group-hover:text-white transition">
                            Explorar <i class="fa-solid fa-arrow-right ml-1.5"></i>
                        </span>
                    </div>

                </div>
            </div>

            <!-- VIEW 2: SUBCATEGORIES / PRODUCTS -->
            <div id="view-catalog" class="hidden animate-fade-in">
                <div class="flex flex-col md:flex-row md:items-center justify-between mb-8 gap-4">
                    <div>
                        <h2 id="catalog-title" class="text-3xl font-bold text-white">Subcategorías</h2>
                        <p id="catalog-subtitle" class="text-slate-400 text-sm">Selecciona una sección o visualiza todos los productos</p>
                    </div>
                    <div id="subcat-filters" class="flex flex-wrap gap-2"></div>
                </div>

                <div id="product-grid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6"></div>
            </div>

        </main>

        <div id="cart-modal" class="fixed inset-0 z-50 bg-black/70 backdrop-blur-sm hidden items-center justify-end transition-opacity">
            <div class="bg-slate-900 border-l border-slate-800 w-full max-w-md h-full flex flex-col shadow-2xl animate-fade-in">
                <div class="p-4 border-b border-slate-800 flex items-center justify-between">
                    <h3 class="text-lg font-bold text-white flex items-center space-x-2">
                        <i class="fa-solid fa-cart-shopping text-brand-500"></i>
                        <span>Tu Carrito de Compras</span>
                    </h3>
                    <button onclick="closeCartModal()" class="w-8 h-8 rounded-full bg-slate-800 hover:bg-slate-700 flex items-center justify-center text-slate-400 hover:text-white transition">
                        <i class="fa-solid fa-xmark"></i>
                    </button>
                </div>

                <div id="cart-items-list" class="flex-grow overflow-y-auto p-4 space-y-3"></div>

                <div class="p-4 border-t border-slate-800 bg-slate-950/50 space-y-4">
                    <div class="space-y-2 text-sm">
                        <div class="flex justify-between text-slate-400">
                            <span>Subtotal</span>
                            <span id="cart-subtotal" class="font-semibold text-slate-200">$0.00</span>
                        </div>
                        <div class="flex justify-between text-slate-400">
                            <span>Delivery / Retiro</span>
                            <span class="text-emerald-400 font-semibold">Gratis</span>
                        </div>
                        <div class="flex justify-between text-lg font-bold text-white pt-2 border-t border-slate-800">
                            <span>Total</span>
                            <span id="cart-total" class="text-brand-400">$0.00</span>
                        </div>
                    </div>

                    <button onclick="proceedToWhatsApp()" class="w-full bg-gradient-to-r from-emerald-600 to-green-600 hover:from-emerald-500 hover:to-green-500 text-white font-bold py-3 px-4 rounded-xl shadow-lg shadow-emerald-600/30 transition transform active:scale-98 flex items-center justify-center space-x-2">
                        <i class="fa-brands fa-whatsapp text-lg"></i>
                        <span>Proceder con la compra</span>
                    </button>
                </div>
            </div>
        </div>

        <!-- Notification / Status Modal -->
        <div id="notification-modal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm hidden items-center justify-center p-4">
            <div class="bg-slate-900 border border-slate-800 rounded-3xl max-w-md w-full p-6 shadow-2xl animate-fade-in">
                <div id="notification-content"></div>
            </div>
        </div>

        <footer class="bg-slate-950 border-t border-slate-800/80 py-6 text-center text-xs text-slate-500">
            <p>© 2026 Mis 3 Ángeles. Todos los derechos reservados.</p>
            <p class="mt-1 text-rose-400/80 font-medium">Calidad y variedad al mejor precio.</p>
        </footer>

    </div>

    <script>
        const storeData = {
            viveres: {
                title: "Víveres",
                subcategories: ["Todos", "Harinas y Granos", "Aceites y Condimentos", "Cereales y Azúcar", "Enlatados"],
                products: [
                    { id: 1, name: "Harina de Maíz Precocida 1kg", subcat: "Harinas y Granos", price: 1.20, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Harina+Maiz" },
                    { id: 2, name: "Arroz Blanco Grano Mediano 1kg", subcat: "Harinas y Granos", price: 1.10, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Arroz+Blanco" },
                    { id: 3, name: "Caraotas Negras 1kg", subcat: "Harinas y Granos", price: 1.80, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Caraotas" },
                    { id: 4, name: "Aceite Vegetal 900ml", subcat: "Aceites y Condimentos", price: 2.50, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Aceite+Vegetal" },
                    { id: 5, name: "Azúcar Refinada 1kg", subcat: "Cereales y Azúcar", price: 1.30, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Azucar" },
                    { id: 6, name: "Sardinas en Salsa de Tomate 170g", subcat: "Enlatados", price: 0.90, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Sardinas" },
                    { id: 7, name: "Atún en Aceite 140g", subcat: "Enlatados", price: 1.60, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Atun+Enlatado" },
                    { id: 8, name: "Pasta Corta 500g", subcat: "Cereales y Azúcar", price: 1.00, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Pasta" }
                ]
            },
            charcuteria: {
                title: "Charcutería",
                subcategories: ["Todos", "Quesos", "Jamones y Embutidos", "Cremas y Aderezos"],
                products: [
                    { id: 9, name: "Queso Blanco Duro 500g", subcat: "Quesos", price: 3.50, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Queso+Duro" },
                    { id: 10, name: "Queso Amarillo Gouda 250g", subcat: "Quesos", price: 2.80, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Queso+Amarillo" },
                    { id: 11, name: "Jamón de Pierna 250g", subcat: "Jamones y Embutidos", price: 2.20, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Jamon+Pierna" },
                    { id: 12, name: "Salchichas Ahumadas Paquete 6uds", subcat: "Jamones y Embutidos", price: 2.00, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Salchichas" },
                    { id: 13, name: "Mortadela Especial con Pimienta 250g", subcat: "Jamones y Embutidos", price: 1.50, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Mortadela" },
                    { id: 14, name: "Mayonesa 400g", subcat: "Cremas y Aderezos", price: 2.30, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Mayonesa" }
                ]
            },
            golosinas: {
                title: "Golosinas",
                subcategories: ["Todos", "Chocolates", "Galletas", "Chupetas y Caramelos", "Snacks Salados"],
                products: [
                    { id: 15, name: "Chocolate con Leche 100g", subcat: "Chocolates", price: 1.50, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Chocolate" },
                    { id: 16, name: "Galletas Dulces Surtidas 200g", subcat: "Galletas", price: 1.20, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Galletas" },
                    { id: 17, name: "Caramelos Surtidos Frutales 100g", subcat: "Chupetas y Caramelos", price: 0.80, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Caramelos" },
                    { id: 18, name: "Papas Fritas Crujientes 45g", subcat: "Snacks Salados", price: 1.00, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Papas+Fritas" },
                    { id: 19, name: "Chupetas de Frutas (Bolsa x10)", subcat: "Chupetas y Caramelos", price: 1.10, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Chupetas" }
                ]
            },
            ferreteria: {
                title: "Ferretería",
                subcategories: ["Todos", "Iluminación", "Herramientas Manuales", "Cintas y Adhesivos"],
                products: [
                    { id: 20, name: "Bombillo LED 12W Luz Blanca", subcat: "Iluminación", price: 2.00, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Bombillo+LED" },
                    { id: 21, name: "Cinta Aislante Electricista", subcat: "Cintas y Adhesivos", price: 0.80, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Cinta+Aislante" },
                    { id: 22, name: "Destornillador Punta de Paleta / Estría", subcat: "Herramientas Manuales", price: 2.50, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Destornillador" },
                    { id: 23, name: "Cinta Adhesiva Transparente Multiuso", subcat: "Cintas y Adhesivos", price: 1.10, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Cinta+Adhesiva" },
                    { id: 24, name: "Teipe Tegui / Cinta Americana", subcat: "Cintas y Adhesivos", price: 3.00, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Teipe" }
                ]
            },
            licores: {
                title: "Licores",
                subcategories: ["Todos", "Cervezas", "Rones y Aguardientes", "Vinos"],
                products: [
                    { id: 25, name: "Cerveza Lata 355ml (Pack x6)", subcat: "Cervezas", price: 5.50, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Cervezas+Pack" },
                    { id: 26, name: "Ron Añejo Botella 0.75L", subcat: "Rones y Aguardientes", price: 12.00, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Ron+Anejo" },
                    { id: 27, name: "Aguardiente Nacional 0.75L", subcat: "Rones y Aguardientes", price: 7.50, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Aguardiente" },
                    { id: 28, name: "Vino Tinto de Mesa 0.75L", subcat: "Vinos", price: 8.00, img: "https://placehold.co/300x200/1e293b/f43f5e?text=Vino+Tinto" }
                ]
            }
        };

        let currentCategory = null;
        let currentSubcat = "Todos";
        let cart = [];

        window.onload = function() {
            setTimeout(() => {
                const loadingBar = document.getElementById('loading-bar');
                if (loadingBar) loadingBar.style.width = '100%';
            }, 100);

            setTimeout(() => {
                const intro = document.getElementById('intro-screen');
                if (intro) {
                    intro.style.opacity = '0';
                    setTimeout(() => {
                        intro.style.display = 'none';
                        const app = document.getElementById('app-container');
                        if (app) app.classList.remove('opacity-0');
                    }, 600);
                }
            }, 1800);
        };

        function selectCategory(catKey) {
            currentCategory = catKey;
            currentSubcat = "Todos";
            
            const catData = storeData[catKey];
            if (!catData) return;

            document.getElementById('catalog-title').innerText = catData.title;
            const breadcrumbContainer = document.getElementById('breadcrumb-container');
            breadcrumbContainer.classList.remove('hidden');
            breadcrumbContainer.classList.add('flex');
            document.getElementById('breadcrumb-current').innerText = catData.title;

            renderSubcatFilters(catData.subcategories);
            renderProducts();

            document.getElementById('view-categories').classList.add('hidden');
            document.getElementById('view-catalog').classList.remove('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function renderSubcatFilters(subcats) {
            const container = document.getElementById('subcat-filters');
            container.innerHTML = '';

            subcats.forEach(sub => {
                const btn = document.createElement('button');
                const isActive = sub === currentSubcat;
                btn.className = `px-4 py-2 rounded-xl text-xs font-semibold transition border ${
                    isActive 
                    ? 'bg-brand-600 text-white border-brand-500 shadow-md shadow-brand-600/30' 
                    : 'bg-slate-800 text-slate-300 border-slate-700 hover:bg-slate-700'
                }`;
                btn.innerText = sub;
                btn.onclick = () => {
                    currentSubcat = sub;
                    renderSubcatFilters(subcats);
                    renderProducts();
                };
                container.appendChild(btn);
            });
        }

        function renderProducts() {
            const grid = document.getElementById('product-grid');
            grid.innerHTML = '';

            const catData = storeData[currentCategory];
            if (!catData) return;

            const filtered = catData.products.filter(p => {
                if (currentSubcat === "Todos") return true;
                return p.subcat === currentSubcat;
            });

            if (filtered.length === 0) {
                grid.innerHTML = `
                    <div class="col-span-full text-center py-12 text-slate-400">
                        <i class="fa-solid fa-box-open text-4xl mb-3 text-slate-600"></i>
                        <p>No hay productos disponibles en esta sección.</p>
                    </div>
                `;
                return;
            }

            filtered.forEach(product => {
                const card = document.createElement('div');
                card.className = "bg-slate-800/80 border border-slate-700/80 rounded-2xl overflow-hidden shadow-lg flex flex-col group hover:border-brand-500/60 transition duration-300";
                card.innerHTML = `
                    <div class="relative overflow-hidden bg-slate-900 h-40">
                        <img src="${product.img}" alt="${product.name}" class="w-full h-full object-cover group-hover:scale-105 transition duration-500" onerror="this.src='https://placehold.co/300x200/1e293b/f43f5e?text=Producto'">
                        <span class="absolute top-2 right-2 bg-slate-950/80 backdrop-blur-md text-rose-400 text-xs font-semibold px-2.5 py-1 rounded-lg border border-slate-800">
                            ${product.subcat}
                        </span>
                    </div>
                    <div class="p-4 flex flex-col flex-grow">
                        <h4 class="font-semibold text-white mb-1 line-clamp-2 text-sm">${product.name}</h4>
                        <div class="mt-auto pt-4 flex items-center justify-between">
                            <span class="text-lg font-bold text-brand-400">$${product.price.toFixed(2)}</span>
                            <button onclick="addToCart(${product.id})" class="bg-brand-600 hover:bg-brand-500 text-white w-9 h-9 rounded-xl flex items-center justify-center transition shadow-md shadow-brand-600/30 active:scale-95">
                                <i class="fa-solid fa-plus text-sm"></i>
                            </button>
                        </div>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function goToHome() {
            currentCategory = null;
            const breadcrumb = document.getElementById('breadcrumb-container');
            breadcrumb.classList.add('hidden');
            breadcrumb.classList.remove('flex');
            document.getElementById('view-catalog').classList.add('hidden');
            document.getElementById('view-categories').classList.remove('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function addToCart(productId) {
            let foundProduct = null;
            for (let cat in storeData) {
                const found = storeData[cat].products.find(p => p.id === productId);
                if (found) {
                    foundProduct = found;
                    break;
                }
            }

            if (!foundProduct) return;

            const existingItem = cart.find(item => item.id === productId);
            if (existingItem) {
                existingItem.qty += 1;
            } else {
                cart.push({ ...foundProduct, qty: 1 });
            }

            updateCartBadge();
            showToast(`¡${foundProduct.name} agregado al carrito!`);
        }

        function updateCartBadge() {
            const totalCount = cart.reduce((sum, item) => sum + item.qty, 0);
            const badge = document.getElementById('cart-badge');
            if (badge) badge.innerText = totalCount;
        }

        function openCartModal() {
            renderCartItems();
            const modal = document.getElementById('cart-modal');
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }

        function closeCartModal() {
            const modal = document.getElementById('cart-modal');
            modal.classList.add('hidden');
            modal.classList.remove('flex');
        }

        function renderCartItems() {
            const list = document.getElementById('cart-items-list');
            list.innerHTML = '';

            if (cart.length === 0) {
                list.innerHTML = `
                    <div class="text-center py-16 text-slate-500">
                        <i class="fa-solid fa-cart-arrow-down text-4xl mb-3"></i>
                        <p class="text-sm">Tu carrito está vacío</p>
                    </div>
                `;
                document.getElementById('cart-subtotal').innerText = '$0.00';
                document.getElementById('cart-total').innerText = '$0.00';
                return;
            }

            let subtotal = 0;

            cart.forEach(item => {
                subtotal += item.price * item.qty;
                const row = document.createElement('div');
                row.className = "flex items-center justify-between bg-slate-800/60 p-3 rounded-2xl border border-slate-700/60";
                row.innerHTML = `
                    <div class="flex-grow pr-3">
                        <h5 class="text-sm font-semibold text-white line-clamp-1">${item.name}</h5>
                        <span class="text-xs text-brand-400 font-medium">$${item.price.toFixed(2)} c/u</span>
                    </div>
                    <div class="flex items-center space-x-2">
                        <button onclick="changeQty(${item.id}, -1)" class="w-7 h-7 bg-slate-700 hover:bg-slate-600 rounded-lg flex items-center justify-center text-xs transition">
                            <i class="fa-solid fa-minus"></i>
                        </button>
                        <span class="text-sm font-bold w-5 text-center">${item.qty}</span>
                        <button onclick="changeQty(${item.id}, 1)" class="w-7 h-7 bg-slate-700 hover:bg-slate-600 rounded-lg flex items-center justify-center text-xs transition">
                            <i class="fa-solid fa-plus"></i>
                        </button>
                    </div>
                `;
                list.appendChild(row);
            });

            document.getElementById('cart-subtotal').innerText = `$${subtotal.toFixed(2)}`;
            document.getElementById('cart-total').innerText = `$${subtotal.toFixed(2)}`;
        }

        function changeQty(productId, delta) {
            const index = cart.findIndex(item => item.id === productId);
            if (index !== -1) {
                cart[index].qty += delta;
                if (cart[index].qty <= 0) {
                    cart.splice(index, 1);
                }
            }
            updateCartBadge();
            renderCartItems();
        }

        function proceedToWhatsApp() {
            if (cart.length === 0) {
                showToast("Agrega productos antes de comprar.");
                return;
            }

            closeCartModal();

            let message = `¡Hola! 👋 Vengo de la tienda *Mis 3 Ángeles*. Me gustaría realizar el siguiente pedido:\n\n`;
            let total = 0;

            cart.forEach(item => {
                const sub = item.price * item.qty;
                total += sub;
                message += `• ${item.qty}x ${item.name} ($${item.price.toFixed(2)} c/u) = *$${sub.toFixed(2)}*\n`;
            });

            message += `\n*Total estimado:* *$${total.toFixed(2)}*`;

            const whatsappNumber = "584245245713";
            const encodedMessage = encodeURIComponent(message);
            const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${encodedMessage}`;

            const notifModal = document.getElementById('notification-modal');
            const content = document.getElementById('notification-content');

            content.innerHTML = `
                <div class="text-center py-6">
                    <div class="w-16 h-16 bg-emerald-500/20 text-emerald-400 rounded-full flex items-center justify-center mx-auto mb-4 text-3xl animate-bounce">
                        <i class="fa-brands fa-whatsapp"></i>
                    </div>
                    <h3 class="text-2xl font-bold text-white mb-2">¡Redirigiendo a WhatsApp!</h3>
                    <p class="text-slate-300 text-sm mb-6">Tu pedido ha sido preparado. Abriendo WhatsApp para enviar los detalles al comercio...</p>
                    <a href="${whatsappUrl}" target="_blank" onclick="resetStoreAfterOrder()" class="block w-full bg-emerald-600 hover:bg-emerald-500 text-white font-semibold py-3 rounded-xl text-sm transition shadow-lg text-center">
                        Abrir WhatsApp Ahora <i class="fa-solid fa-arrow-right ml-1"></i>
                    </a>
                </div>
            `;
            
            notifModal.classList.remove('hidden');
            notifModal.classList.add('flex');

            setTimeout(() => {
                window.open(whatsappUrl, '_blank');
            }, 600);
        }

        function resetStoreAfterOrder() {
            cart = [];
            updateCartBadge();
            closeNotificationModal();
            goToHome();
        }

        function closeNotificationModal() {
            const modal = document.getElementById('notification-modal');
            if (modal) {
                modal.classList.add('hidden');
                modal.classList.remove('flex');
            }
        }

        function showToast(message) {
            const existingToast = document.getElementById('toast-notification');
            if (existingToast) existingToast.remove();

            const toast = document.createElement('div');
            toast.id = 'toast-notification';
            toast.className = "fixed bottom-6 right-6 z-50 bg-slate-800 border border-brand-500/50 text-white px-4 py-3 rounded-2xl shadow-2xl flex items-center space-x-3 animate-fade-in";
            toast.innerHTML = `
                <div class="w-8 h-8 bg-brand-600 rounded-xl flex items-center justify-center text-white">
                    <i class="fa-solid fa-bell"></i>
                </div>
                <span class="text-sm font-medium">${message}</span>
            `;
            document.body.appendChild(toast);

            setTimeout(() => {
                toast.style.opacity = '0';
                toast.style.transition = 'opacity 0.5s ease';
                setTimeout(() => toast.remove(), 500);
            }, 3000);
        }
    </script>
</body>
</html>

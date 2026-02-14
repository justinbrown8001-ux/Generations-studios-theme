<!-- ==================== NAVIGATION ==================== -->
<nav class="fixed top-0 w-full bg-[#0a0a0a]/90 backdrop-blur-md border-b border-white/5 z-50 transition-all duration-300" id="navbar">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="flex justify-between items-center h-20">
            <!-- Logo -->
            <div class="flex-shrink-0 cursor-pointer" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">
                <a href="{{ routes.root_url }}" class="text-lg font-bold tracking-[0.2em] uppercase">
                    Generations<span class="font-light opacity-60">Studios</span>
                </a>
            </div>
            
            <!-- Desktop Menu -->
            <div class="hidden md:flex space-x-10">
                <a href="#home" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Home</a>
                <a href="#calendar" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Calendar</a>
                <a href="#lab" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Creative Lab</a>
                <a href="#shop" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Shop</a>
            </div>
            
            <!-- Icons -->
            <div class="flex items-center space-x-6">
                <button class="text-gray-400 hover:text-white transition-colors" onclick="toggleSearch()">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                </button>
                <button class="text-gray-400 hover:text-white transition-colors relative" onclick="toggleCart()">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg>
                    <span id="cart-badge" class="absolute -top-2 -right-2 bg-white text-black text-[10px] w-4 h-4 rounded-full flex items-center justify-center {% if cart.item_count == 0 %}hidden{% endif %} font-bold">{{ cart.item_count }}</span>
                </button>
                <button class="md:hidden text-gray-400 hover:text-white" onclick="toggleMobileMenu()">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 6h16M4 12h16M4 18h16"></path></svg>
                </button>
            </div>
        </div>
    </div>
    
    <!-- Mobile Menu -->
    <div id="mobile-menu" class="hidden md:hidden bg-[#0a0a0a] border-t border-white/5 animate-slide-in">
        <div class="px-6 py-6 space-y-4">
            <a href="#home" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Home</a>
            <a href="#calendar" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Calendar</a>
            <a href="#lab" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Creative Lab</a>
            <a href="#shop" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Shop</a>
        </div>
    </div>
</nav>

<!-- ==================== HERO SECTION ==================== -->
<section id="home" class="relative pt-20 min-h-screen flex items-center bg-[#0a0a0a] overflow-hidden">
    <div class="absolute inset-0 z-0">
        <div class="absolute inset-0 bg-gradient-to-b from-transparent via-[#0a0a0a]/50 to-[#0a0a0a]"></div>
        {% if section.settings.hero_image %}
            {{ section.settings.hero_image | image_url: width: 1920 | image_tag: class: 'w-full h-full object-cover opacity-40 grayscale', alt: 'Hero background' }}
        {% else %}
            <img src="https://images.unsplash.com/photo-1552374196-1ab2a1c593e8?w=1920&q=80" alt="Dark fashion" class="w-full h-full object-cover opacity-40 grayscale">
        {% endif %}
    </div>
    
    <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-8 py-32 w-full">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
            <div class="animate-fade-in">
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-6">Est. 2024</p>
                <h1 class="text-6xl md:text-8xl font-bold tracking-tighter mb-8 leading-[0.9]">
                    {{ section.settings.heading_line1 | default: 'SUSTAINABILITY' }}<br>
                    <span class="text-stroke">{{ section.settings.heading_line2 | default: 'FOR MODERN' }}</span><br>
                    {{ section.settings.heading_line3 | default: 'CONSUMERS' }}
                </h1>
                <p class="text-gray-400 text-lg mb-10 max-w-md leading-relaxed">
                    {{ section.settings.hero_description | default: 'We specialize in crafting cutting-edge lifestyle experiences. Minimalist essentials meet dark innovation.' }}
                </p>
                <div class="flex flex-col sm:flex-row gap-4">
                    <a href="#shop" class="btn-primary px-10 py-4 text-xs font-bold tracking-widest uppercase text-center inline-block">
                        Explore Collection
                    </a>
                    <a href="#calendar" class="btn-outline px-10 py-4 text-xs font-bold tracking-widest uppercase text-center inline-block">
                        View Calendar
                    </a>
                </div>
            </div>
            
            <div class="hidden lg:block relative">
                <div class="grid grid-cols-2 gap-4">
                    <div class="space-y-4 mt-12">
                        <div class="img-zoom aspect-[3/4] bg-[#111]">
                            <img src="https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 1">
                        </div>
                        <div class="img-zoom aspect-square bg-[#111]">
                            <img src="https://images.unsplash.com/photo-1503341504253-dff4815485f1?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 2">
                        </div>
                    </div>
                    <div class="space-y-4">
                        <div class="img-zoom aspect-square bg-[#111]">
                            <img src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 3">
                        </div>
                        <div class="img-zoom aspect-[3/4] bg-[#111]">
                            <img src="https://images.unsplash.com/photo-1509631179647-0177331693ae?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 4">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Scroll Indicator -->
    <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
        <svg class="w-6 h-6 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== BRAND STORY SECTION ==================== -->
<section class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
            <div class="order-2 lg:order-1">
                <div class="img-zoom aspect-[4/5] bg-[#111] relative">
                    {% if section.settings.story_image %}
                        {{ section.settings.story_image | image_url: width: 800 | image_tag: class: 'w-full h-full object-cover', alt: 'Brand story' }}
                    {% else %}
                        <img src="https://images.unsplash.com/photo-1558171813-4c088753af8f?w=800&q=80" class="w-full h-full object-cover" alt="Brand story">
                    {% endif %}
                    <div class="absolute bottom-6 left-6 bg-white text-black px-4 py-2 text-xs font-bold tracking-widest uppercase">
                        Since 2024
                    </div>
                </div>
            </div>
            <div class="order-1 lg:order-2">
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Our Philosophy</p>
                <h2 class="text-4xl md:text-6xl font-bold tracking-tighter mb-8">
                    UNVEILING EXCLUSIVE<br>
                    <span class="text-gray-500">STORY ABOUT</span><br>
                    OUR BRAND
                </h2>
                <p class="text-gray-400 leading-relaxed mb-8 max-w-lg">
                    Every piece is a narrative woven from sustainable materials and dark aesthetics. We don't follow trends—we engineer timeless essentials for the modern urban landscape.
                </p>
                <div class="flex items-center gap-8 text-xs tracking-widest uppercase text-gray-500">
                    <div>
                        <span class="block text-2xl font-bold text-white mb-1">50+</span>
                        AI Generated Drops
                    </div>
                    <div>
                        <span class="block text-2xl font-bold text-white mb-1">100%</span>
                        Sustainable
                    </div>
                    <div>
                        <span class="block text-2xl font-bold text-white mb-1">24h</span>
                        Global Shipping
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== DROP CALENDAR SECTION ==================== -->
<section id="calendar" class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="mb-20">
            <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Studio Schedule</p>
            <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">DROP CALENDAR</h2>
        </div>
        
        <div class="grid lg:grid-cols-3 gap-8">
            <!-- Calendar -->
            <div class="lg:col-span-1 bg-[#111] border border-white/5 p-8">
                <div class="flex justify-between items-center mb-8">
                    <h3 class="text-sm font-bold tracking-widest uppercase">February 2026</h3>
                    <div class="flex gap-2">
                        <button class="p-2 hover:bg-white/5 rounded transition-colors text-gray-400 hover:text-white" onclick="changeMonth(-1)">‹</button>
                        <button class="p-2 hover:bg-white/5 rounded transition-colors text-gray-400 hover:text-white" onclick="changeMonth(1)">›</button>
                    </div>
                </div>
                <div class="grid grid-cols-7 gap-1 text-center text-xs mb-4 text-gray-600 uppercase tracking-wider">
                    <div>Su</div><div>Mo</div><div>Tu</div><div>We</div><div>Th</div><div>Fr</div><div>Sa</div>
                </div>
                <div class="calendar-grid" id="calendar-grid"></div>
                <div class="mt-8 flex items-center gap-6 text-xs text-gray-500 uppercase tracking-wider">
                    <div class="flex items-center gap-2">
                        <div class="w-2 h-2 bg-white rounded-full"></div>
                        <span>Drop Day</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <div class="w-2 h-2 bg-gray-700 rounded-full"></div>
                        <span>Regular</span>
                    </div>
                </div>
            </div>
            
            <!-- Selected Drop Display -->
            <div class="lg:col-span-2">
                <div id="drop-display" class="h-full bg-[#111] border border-white/5 overflow-hidden relative group cursor-pointer">
                    <img id="drop-image" src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=1200&q=80" class="w-full h-full object-cover opacity-60 grayscale group-hover:grayscale-0 transition-all duration-700" alt="Drop preview">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent"></div>
                    <div class="absolute inset-0 p-10 flex flex-col justify-end">
                        <span class="inline-block px-3 py-1 bg-white text-black text-[10px] font-bold tracking-widest uppercase mb-4 w-fit">Upcoming Drop</span>
                        <h3 id="drop-title" class="text-3xl md:text-5xl font-bold tracking-tighter mb-4">Midnight Cotton Collection</h3>
                        <p id="drop-desc" class="text-gray-400 mb-6 max-w-lg text-sm leading-relaxed">AI-generated urban lifestyle photography featuring our heavyweight cotton essentials in monochromatic settings.</p>
                        <div class="flex items-center gap-6">
                            <span id="drop-date" class="text-sm tracking-widest uppercase text-gray-500">Feb 15, 2026</span>
                            <a href="#shop" class="px-8 py-3 bg-white text-black text-xs font-bold tracking-widest uppercase hover:bg-gray-200 transition-colors inline-block">
                                Preview
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== CREATIVE LAB SECTION ==================== -->
<section id="lab" class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="mb-20">
            <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Knowledge Base</p>
            <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">CREATIVE LAB</h2>
        </div>
        
        <!-- Tabs -->
        <div class="flex gap-8 mb-16 border-b border-white/10 pb-6 overflow-x-auto">
            <button onclick="switchTab('stories')" id="tab-stories" class="text-sm font-bold tracking-widest uppercase text-white whitespace-nowrap relative pb-6">
                Design Stories
                <span class="absolute bottom-0 left-0 w-full h-0.5 bg-white"></span>
            </button>
            <button onclick="switchTab('fabric')" id="tab-fabric" class="text-sm font-bold tracking-widest uppercase text-gray-500 hover:text-white transition-colors whitespace-nowrap relative pb-6">
                Fabric Education
            </button>
            <button onclick="switchTab('styling')" id="tab-styling" class="text-sm font-bold tracking-widest uppercase text-gray-500 hover:text-white transition-colors whitespace-nowrap relative pb-6">
                Styling Guides
            </button>
        </div>
        
        <!-- Tab Content: Design Stories -->
        <div class="tab-content active" id="content-stories">
            <div class="grid md:grid-cols-3 gap-6">
                <article class="product-card cursor-pointer group">
                    <div class="aspect-[4/3] overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1558171813-4c088753af8f?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Design process">
                    </div>
                    <div class="p-6">
                        <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Process</span>
                        <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">The Art of Minimalism</h3>
                        <p class="text-gray-400 text-sm leading-relaxed mb-4">How we strip away the unnecessary to focus on form, function, and timeless appeal.</p>
                        <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                            Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                        </span>
                    </div>
                </article>
                
                <article class="product-card cursor-pointer group">
                    <div class="aspect-[4/3] overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1441986300917-64674bd600d8?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Studio">
                    </div>
                    <div class="p-6">
                        <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Behind the Scenes</span>
                        <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">Studio Sessions</h3>
                        <p class="text-gray-400 text-sm leading-relaxed mb-4">A look inside our creative process, from initial sketches to final production.</p>
                        <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                            Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                        </span>
                    </div>
                </article>
                
                <article class="product-card cursor-pointer group">
                    <div class="aspect-[4/3] overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Sustainability">
                    </div>
                    <div class="p-6">
                        <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Sustainability</span>
                        <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">Zero Waste Journey</h3>
                        <p class="text-gray-400 text-sm leading-relaxed mb-4">Our commitment to eliminating waste through innovative pattern making.</p>
                        <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                            Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                        </span>
                    </div>
                </article>
            </div>
        </div>
        
        <!-- Tab Content: Fabric Education -->
        <div class="tab-content" id="content-fabric">
            <div class="grid md:grid-cols-2 gap-8">
                <div class="product-card p-8">
                    <h3 class="text-2xl font-bold mb-8 tracking-tight">Fabric Glossary</h3>
                    <div class="space-y-8">
                        <div class="flex gap-6 pb-8 border-b border-white/5">
                            <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🧵</div>
                            <div>
                                <h4 class="font-bold mb-2 tracking-tight">Organic Cotton</h4>
                                <p class="text-sm text-gray-400 leading-relaxed">Grown without synthetic pesticides, our organic cotton uses 91% less water than conventional cotton farming.</p>
                            </div>
                        </div>
                        <div class="flex gap-6 pb-8 border-b border-white/5">
                            <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🧶</div>
                            <div>
                                <h4 class="font-bold mb-2 tracking-tight">Recycled Fleece</h4>
                                <p class="text-sm text-gray-400 leading-relaxed">Made from post-consumer plastic bottles, transformed into ultra-soft fleece with superior warmth.</p>
                            </div>
                        </div>
                        <div class="flex gap-6">
                            <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🪡</div>
                            <div>
                                <h4 class="font-bold mb-2 tracking-tight">Tencel™ Modal</h4>
                                <p class="text-sm text-gray-400 leading-relaxed">Botanical fibers from sustainably harvested beech trees, known for exceptional breathability.</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="bg-gradient-to-br from-[#1a1a1a] to-[#0a0a0a] border border-white/5 p-8 relative overflow-hidden">
                    <div class="absolute top-0 right-0 w-64 h-64 bg-white/5 rounded-full blur-3xl"></div>
                    <div class="relative z-10">
                        <h3 class="text-2xl font-bold mb-8 tracking-tight">Quality Standards</h3>
                        <ul class="space-y-6">
                            <li class="flex items-start gap-4">
                                <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                <div>
                                    <span class="block font-bold mb-1">OEKO-TEX® Standard 100</span>
                                    <span class="text-sm text-gray-400">Certified free from harmful substances</span>
                                </div>
                            </li>
                            <li class="flex items-start gap-4">
                                <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                <div>
                                    <span class="block font-bold mb-1">GOTS Certified Organic</span>
                                    <span class="text-sm text-gray-400">Global Organic Textile Standard</span>
                                </div>
                            </li>
                            <li class="flex items-start gap-4">
                                <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                <div>
                                    <span class="block font-bold mb-1">Bluesign® Approved</span>
                                    <span class="text-sm text-gray-400">Sustainable chemical management</span>
                                </div>
                            </li>
                            <li class="flex items-start gap-4">
                                <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                <div>
                                    <span class="block font-bold mb-1">Fair Trade Certified™</span>
                                    <span class="text-sm text-gray-400">Ethical production standards</span>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Tab Content: Styling Guides -->
        <div class="tab-content" id="content-styling">
            <div class="grid md:grid-cols-3 gap-6">
                <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                    <img src="https://images.unsplash.com/photo-1483985988355-763728e1935b?w=600&q=80" class="w-full h-full object-cover" alt="Styling 1">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                        <div class="absolute bottom-0 left-0 right-0 p-8">
                            <h4 class="font-bold text-xl tracking-tight mb-2">Monochrome Layers</h4>
                            <p class="text-sm text-gray-400">3 ways to style black & white</p>
                        </div>
                    </div>
                </div>
                <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                    <img src="https://images.unsplash.com/photo-1469334031218-e382a71b716b?w=600&q=80" class="w-full h-full object-cover" alt="Styling 2">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                        <div class="absolute bottom-0 left-0 right-0 p-8">
                            <h4 class="font-bold text-xl tracking-tight mb-2">Essential Basics</h4>
                            <p class="text-sm text-gray-400">Building a capsule wardrobe</p>
                        </div>
                    </div>
                </div>
                <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                    <img src="https://images.unsplash.com/photo-1445205170230-053b83016050?w=600&q=80" class="w-full h-full object-cover" alt="Styling 3">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                        <div class="absolute bottom-0 left-0 right-0 p-8">
                            <h4 class="font-bold text-xl tracking-tight mb-2">Street Style</h4>
                            <p class="text-sm text-gray-400">Urban minimalism guide</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== SHOP SECTION ==================== -->
<section id="shop" class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="flex flex-col md:flex-row md:items-end md:justify-between mb-20 gap-8">
            <div>
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Collection</p>
                <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">OUR BESTSELLER</h2>
            </div>
            
            <!-- Category Filter -->
            <div class="flex gap-4 flex-wrap">
                <button onclick="filterProducts('all')" class="filter-btn active px-6 py-3 bg-white text-black text-xs font-bold tracking-widest uppercase transition-all" data-filter="all">All</button>
                <button onclick="filterProducts('hoodies')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="hoodies">Hoodies</button>
                <button onclick="filterProducts('tshirts')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="tshirts">T-Shirts</button>
                <button onclick="filterProducts('posters')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="posters">Silver Posters</button>
            </div>
        </div>
        
        <!-- Products Grid -->
        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6" id="products-grid">
            {% for product in collections.all.products limit: 8 %}
                <div class="product-card group cursor-pointer animate-fade-in" data-category="{{ product.type | handle | default: 'all' }}">
                    <div class="aspect-[4/5] overflow-hidden relative bg-[#111]">
                        {% if product.featured_image %}
                            {{ product.featured_image | image_url: width: 600 | image_tag: class: 'w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105', alt: product.title }}
                        {% else %}
                            <img src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=600&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="{{ product.title }}">
                        {% endif %}
                        
                        {% if product.available %}
                            <button onclick="addToCart({{ product.variants.first.id }})" class="absolute bottom-4 right-4 w-12 h-12 bg-white text-black rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transform translate-y-2 group-hover:translate-y-0 transition-all duration-300 hover:bg-gray-200">
                                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                            </button>
                        {% endif %}
                        
                        {% if product.tags contains 'Limited' %}
                            <span class="absolute top-4 left-4 px-3 py-1 bg-white text-black text-[10px] font-bold tracking-widest uppercase">Limited</span>
                        {% endif %}
                        
                        {% unless product.available %}
                            <span class="absolute top-4 left-4 px-3 py-1 bg-gray-800 text-white text-[10px] font-bold tracking-widest uppercase">Sold Out</span>
                        {% endunless %}
                    </div>
                    <div class="p-6">
                        <h3 class="font-bold text-sm mb-2 tracking-tight group-hover:text-gray-300 transition-colors">{{ product.title }}</h3>
                        <p class="text-gray-500 text-xs mb-3 line-clamp-1">{{ product.description | strip_html | truncate: 60 }}</p>
                        <p class="font-bold text-sm">{{ product.price | money }}</p>
                    </div>
                </div>
            {% endfor %}
        </div>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== SERVICES SECTION ==================== -->
<section class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
            <div>
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">What We Offer</p>
                <h2 class="text-4xl md:text-5xl font-bold tracking-tighter mb-12">OUR SERVICES</h2>
                
                <div class="space-y-8">
                    <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                        <div class="flex items-center gap-4">
                            <span class="text-gray-500 text-sm">01</span>
                            <span class="font-bold tracking-wide">Global Shipping</span>
                        </div>
                        <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                    </div>
                    <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                        <div class="flex items-center gap-4">
                            <span class="text-gray-500 text-sm">02</span>
                            <span class="font-bold tracking-wide">AI Design Consultation</span>
                        </div>
                        <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                    </div>
                    <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                        <div class="flex items-center gap-4">
                            <span class="text-gray-500 text-sm">03</span>
                            <span class="font-bold tracking-wide">Custom Branding</span>
                        </div>
                        <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                    </div>
                    <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                        <div class="flex items-center gap-4">
                            <span class="text-gray-500 text-sm">04</span>
                            <span class="font-bold tracking-wide">24/7 Support</span>
                        </div>
                        <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                    </div>
                </div>
            </div>
            
            <div class="relative">
                <div class="img-zoom aspect-[4/5] bg-[#111]">
                    <img src="https://images.unsplash.com/photo-1552374196-1ab2a1c593e8?w=800&q=80" class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700" alt="Services">
                </div>
                <div class="absolute -bottom-6 -left-6 bg-white text-black p-6 max-w-xs">
                    <p class="text-xs font-bold tracking-widest uppercase mb-2">Premium Service</p>
                    <p class="text-sm font-medium">White-glove treatment for every order, from studio to doorstep.</p>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- ==================== NEWSLETTER SECTION ==================== -->
<section class="py-32 bg-[#111] border-y border-white/5">
    <div class="max-w-4xl mx-auto px-6 lg:px-8 text-center">
        <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Stay Updated</p>
        <h2 class="text-3xl md:text-5xl font-bold tracking-tighter mb-8">JOIN THE NEWSLETTER</h2>
        <p class="text-gray-400 mb-10 max-w-lg mx-auto">Be the first to know about exclusive drops, AI-generated collections, and member-only events.</p>
        
        {% form 'customer', class: 'flex flex-col sm:flex-row gap-4 max-w-md mx-auto' %}
            <input 
                type="email" 
                name="contact[email]" 
                placeholder="Enter your email" 
                class="flex-1 px-6 py-4 bg-[#0a0a0a] border border-white/10 text-white placeholder-gray-600 focus:outline-none focus:border-white/30 transition-colors text-sm"
                required
            >
            <button type="submit" class="px-8 py-4 bg-white text-black font-bold text-xs tracking-widest uppercase hover:bg-gray-200 transition-colors">
                Subscribe
            </button>
        {% endform %}
    </div>
</section>

<!-- ==================== FOOTER ==================== -->
<footer class="bg-[#0a0a0a] pt-20 pb-10">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="grid md:grid-cols-4 gap-12 mb-20">
            <div class="md:col-span-2">
                <h3 class="text-lg font-bold tracking-[0.2em] uppercase mb-6">
                    Generations<span class="font-light opacity-60">Studios</span>
                </h3>
                <p class="text-gray-500 text-sm leading-relaxed max-w-sm mb-8">
                    Crafting cutting-edge lifestyle apparel for the modern consumer. Sustainable, minimal, timeless.
                </p>
                <div class="flex gap-4">
                    <a href="#" class="w-10 h-10 border border-white/10 flex items-center justify-center hover:border-white hover:bg-white hover:text-black transition-all">
                        <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/></svg>
                    </a>
                    <a href="#" class="w-10 h-10 border border-white/10 flex items-center justify-center hover:border-white hover:bg-white hover:text-black transition-all">
                        <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
                    </a>
                </div>
            </div>
            <div>
                <h4 class="font-bold text-xs tracking-widest uppercase mb-6 text-gray-400">Shop</h4>
                <ul class="space-y-4 text-sm text-gray-500">
                    <li><a href="#shop" class="hover:text-white transition-colors">New Arrivals</a></li>
                    <li><a href="#shop" class="hover:text-white transition-colors">Best Sellers</a></li>
                    <li><a href="#shop" class="hover:text-white transition-colors">Hoodies</a></li>
                    <li><a href="#shop" class="hover:text-white transition-colors">T-Shirts</a></li>
                    <li><a href="#shop" class="hover:text-white transition-colors">Posters</a></li>
                </ul>
            </div>
            <div>
                <h4 class="font-bold text-xs tracking-widest uppercase mb-6 text-gray-400">Support</h4>
                <ul class="space-y-4 text-sm text-gray-500">
                    <li><a href="#" class="hover:text-white transition-colors">Contact</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Shipping</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Returns</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Size Guide</a></li>
                </ul>
            </div>
        </div>
        
        <div class="border-t border-white/10 pt-8 flex flex-col md:flex-row justify-between items-center gap-4">
            <p class="text-xs text-gray-600">© {{ 'now' | date: '%Y' }} Generations Studios. All rights reserved.</p>
            <div class="flex gap-8 text-xs text-gray-600">
                <a href="#" class="hover:text-white transition-colors">Terms</a>
                <a href="#" class="hover:text-white transition-colors">Privacy</a>
                <a href="#" class="hover:text-white transition-colors">Cookies</a>
            </div>
        </div>
    </div>
</footer>

<!-- ==================== CART SIDEBAR ==================== -->
<div id="cart-sidebar" class="fixed inset-y-0 right-0 w-full md:w-[480px] bg-[#0a0a0a] border-l border-white/10 transform translate-x-full transition-transform duration-500 z-50 flex flex-col">
    <div class="p-8 border-b border-white/10 flex justify-between items-center">
        <h2 class="text-sm font-bold tracking-widest uppercase">Shopping Cart</h2>
        <button onclick="toggleCart()" class="p-2 hover:bg-white/5 rounded-full transition-colors">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
        </button>
    </div>
    
    <div class="flex-1 overflow-y-auto p-8" id="cart-items">
        {% if cart.item_count == 0 %}
            <div class="text-center text-gray-600 mt-20">
                <div class="text-4xl mb-4 opacity-20">🛒</div>
                <p class="text-sm tracking-widest uppercase mb-4">Your cart is empty</p>
                <button onclick="toggleCart(); window.location.href='#shop'" class="text-xs font-bold tracking-widest uppercase text-white hover:text-gray-300 transition-colors border-b border-white/30 pb-1">
                    Start Shopping
                </button>
            </div>
        {% else %}
            {% for item in cart.items %}
                <div class="flex gap-6 mb-8 animate-fade-in">
                    <div class="w-24 h-24 bg-[#111] overflow-hidden flex-shrink-0">
                        {% if item.image %}
                            {{ item.image | image_url: width: 200 | image_tag: class: 'w-full h-full object-cover grayscale', alt: item.title }}
                        {% endif %}
                    </div>
                    <div class="flex-1 flex flex-col justify-between">
                        <div>
                            <h4 class="font-bold text-sm mb-1 tracking-tight">{{ item.product.title }}</h4>
                            <p class="text-gray-500 text-xs">{{ item.price | money }}</p>
                        </div>
                        <div class="flex items-center justify-between">
                            <div class="flex items-center gap-4 border border-white/10 px-4 py-2">
                                <button onclick="updateCartItem({{ item.variant_id }}, {{ item.quantity | minus: 1 }})" class="text-gray-500 hover:text-white transition-colors">−</button>
                                <span class="text-sm font-bold w-4 text-center">{{ item.quantity }}</span>
                                <button onclick="updateCartItem({{ item.variant_id }}, {{ item.quantity | plus: 1 }})" class="text-gray-500 hover:text-white transition-colors">+</button>
                            </div>
                            <button onclick="removeCartItem({{ item.variant_id }})" class="text-gray-600 hover:text-white transition-colors text-xs tracking-widest uppercase">
                                Remove
                            </button>
                        </div>
                    </div>
                </div>
            {% endfor %}
        {% endif %}
    </div>
    
    {% if cart.item_count > 0 %}
    <div class="border-t border-white/10 p-8 bg-[#111]">
        <div class="flex justify-between mb-4 text-sm">
            <span class="text-gray-500 uppercase tracking-wider text-xs">Subtotal</span>
            <span class="font-bold">{{ cart.total_price | money }}</span>
        </div>
        <div class="flex justify-between mb-8 text-sm">
            <span class="text-gray-500 uppercase tracking-wider text-xs">Shipping</span>
            <span class="text-gray-400 text-xs">Calculated at checkout</span>
        </div>
        <div class="flex justify-between mb-8 text-lg font-bold">
            <span class="tracking-tight">Total</span>
            <span>{{ cart.total_price | money }}</span>
        </div>
        <a href="{{ routes.cart_url }}" class="block w-full py-4 bg-white text-black font-bold text-xs tracking-widest uppercase hover:bg-gray-200 transition-all text-center">
            Checkout
        </a>
    </div>
    {% endif %}
</div>

<!-- Overlay -->
<div id="overlay" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-40 hidden opacity-0 transition-opacity duration-500" onclick="toggleCart()"></div>

<!-- ==================== SEARCH MODAL ==================== -->
<div id="search-modal" class="fixed inset-0 bg-[#0a0a0a]/98 backdrop-blur-md z-50 hidden flex items-center justify-center p-6">
    <button onclick="toggleSearch()" class="absolute top-8 right-8 p-2 hover:bg-white/5 rounded-full transition-colors">
        <svg class="w-8 h-8 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
    </button>
    <div class="w-full max-w-3xl">
        <form action="{{ routes.search_url }}" method="get" role="search" class="w-full">
            <input 
                type="search" 
                name="q" 
                placeholder="Search products..." 
                class="w-full text-5xl md:text-7xl font-bold bg-transparent border-b-2 border-white/20 pb-6 focus:outline-none focus:border-white placeholder-gray-800 text-center"
            >
        </form>
        <p class="mt-8 text-center text-gray-500 text-xs tracking-widest uppercase">Press Enter to search</p>
    </div>
</div>

<!-- ==================== JAVASCRIPT ==================== -->
<script>
    // Global Variables
    window.shopUrl = '{{ shop.url }}';
    window.routes = {
        cart_add_url: '{{ routes.cart_add_url }}',
        cart_change_url: '{{ routes.cart_change_url }}',
        cart_update_url: '{{ routes.cart_update_url }}',
        cart_url: '{{ routes.cart_url }}',
        predictive_search_url: '{{ routes.predictive_search_url }}'
    };

    // ==================== NAVIGATION ====================
    function toggleMobileMenu() {
        document.getElementById('mobile-menu').classList.toggle('hidden');
    }

    function toggleSearch() {
        const modal = document.getElementById('search-modal');
        modal.classList.toggle('hidden');
        if (!modal.classList.contains('hidden')) {
            modal.querySelector('input').focus();
        }
    }

    function toggleCart() {
        const sidebar = document.getElementById('cart-sidebar');
        const overlay = document.getElementById('overlay');
        
        if (sidebar.classList.contains('translate-x-full')) {
            sidebar.classList.remove('translate-x-full');
            sidebar.classList.add('translate-x-0');
            overlay.classList.remove('hidden');
            setTimeout(() => overlay.classList.remove('opacity-0'), 10);
            document.body.style.overflow = 'hidden';
        } else {
            sidebar.classList.add('translate-x-full');
            sidebar.classList.remove('translate-x-0');
            overlay.classList.add('opacity-0');
            setTimeout(() => overlay.classList.add('hidden'), 500);
            document.body.style.overflow = '';
        }
    }

    // Navbar scroll effect
    window.addEventListener('scroll', () => {
        const navbar = document.getElementById('navbar');
        if (window.scrollY > 50) {
            navbar.classList.add('bg-[#0a0a0a]/95');
        } else {
            navbar.classList.remove('bg-[#0a0a0a]/95');
        }
    });

    // ==================== CALENDAR ====================
    function generateCalendar() {
        const grid = document.getElementById('calendar-grid');
        const daysInMonth = 28;
        const startDay = 0;
        
        let html = '';
        for (let i = 0; i < startDay; i++) {
            html += '<div class="calendar-day text-gray-800"></div>';
        }
        
        const dropDays = [5, 12, 15, 19, 26];
        for (let i = 1; i <= daysInMonth; i++) {
            const hasDrop = dropDays.includes(i);
            const isSelected = i === 15;
            html += `<div class="calendar-day ${hasDrop ? 'has-drop' : ''} ${isSelected ? 'selected' : ''}" onclick="selectDate(${i})">${i}</div>`;
        }
        
        grid.innerHTML = html;
    }

    function selectDate(day) {
        document.querySelectorAll('.calendar-day').forEach(d => d.classList.remove('selected'));
        event.target.classList.add('selected');
        
        const titles = ['Urban Shadows', 'Midnight Cotton', 'Silver Linings', 'Monochrome Dreams', 'Essential Basics'];
        const images = [
            'https://images.unsplash.com/photo-1503341504253-dff4815485f1?w=1200&q=80',
            'https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=1200&q=80',
            'https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?w=1200&q=80',
            'https://images.unsplash.com/photo-1509631179647-0177331693ae?w=1200&q=80',
            'https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=1200&q=80'
        ];
        
        const index = (day % 5);
        document.getElementById('drop-title').textContent = titles[index] + ' Collection';
        document.getElementById('drop-image').src = images[index];
        document.getElementById('drop-date').textContent = `Feb ${day}, 2026`;
    }

    function changeMonth(delta) {
        const grid = document.getElementById('calendar-grid');
        grid.style.opacity = '0';
        setTimeout(() => {
            generateCalendar();
            grid.style.opacity = '1';
        }, 200);
    }

    // ==================== TABS ====================
    function switchTab(tab) {
        document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
        document.getElementById(`content-${tab}`).classList.add('active');
        
        ['stories', 'fabric', 'styling'].forEach(t => {
            const btn = document.getElementById(`tab-${t}`);
            const indicator = btn.querySelector('span') || document.createElement('span');
            
            if (t === tab) {
                btn.classList.remove('text-gray-500');
                btn.classList.add('text-white');
                if (!btn.querySelector('span')) {
                    indicator.className = 'absolute bottom-0 left-0 w-full h-0.5 bg-white';
                    btn.appendChild(indicator);
                }
            } else {
                btn.classList.add('text-gray-500');
                btn.classList.remove('text-white');
                const existingIndicator = btn.querySelector('span');
                if (existingIndicator) existingIndicator.remove();
            }
        });
    }

    // ==================== PRODUCT FILTER ====================
    function filterProducts(category) {
        const products = document.querySelectorAll('#products-grid > div');
        
        document.querySelectorAll('.filter-btn').forEach(btn => {
            if (btn.dataset.filter === category) {
                btn.classList.add('bg-white', 'text-black', 'border-white');
                btn.classList.remove('text-gray-400', 'border-white/20');
            } else {
                btn.classList.remove('bg-white', 'text-black', 'border-white');
                btn.classList.add('text-gray-400', 'border-white/20');
            }
        });
        
        products.forEach(product => {
            if (category === 'all' || product.dataset.category === category) {
                product.style.display = 'block';
            } else {
                product.style.display = 'none';
            }
        });
    }

    // ==================== CART FUNCTIONS ====================
    async function addToCart(variantId) {
        const formData = {
            'items': [{
                'id': variantId,
                'quantity': 1
            }]
        };
        
        try {
            const response = await fetch(window.routes.cart_add_url, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(formData)
            });
            
            if (response.ok) {
                const cartData = await response.json();
                updateCartUI(cartData);
                toggleCart();
                
                // Animate badge
                const badge = document.getElementById('cart-badge');
                badge.classList.add('cart-bounce');
                setTimeout(() => badge.classList.remove('cart-bounce'), 300);
            }
        } catch (error) {
            console.error('Error adding to cart:', error);
        }
    }

    async function updateCartItem(variantId, quantity) {
        if (quantity < 1) {
            await removeCartItem(variantId);
            return;
        }
        
        try {
            const response = await fetch(window.routes.cart_change_url, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ id: variantId, quantity: quantity })
            });
            
            if (response.ok) {
                window.location.reload();
            }
        } catch (error) {
            console.error('Error updating cart:', error);
        }
    }

    async function removeCartItem(variantId) {
        await updateCartItem(variantId, 0);
    }

    function updateCartUI(cartData) {
        // Refresh the page to show updated cart
        window.location.reload();
    }

    // ==================== INITIALIZATION ====================
    document.addEventListener('DOMContentLoaded', () => {
        generateCalendar();
        
        // Smooth scroll for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });
    });
</script>

{% schema %}
{
    "name": "Generations Studios - Full Theme",
    "settings": [
        {
            "type": "image_picker",
            "id": "hero_image",
            "label": "Hero Background Image"
        },
        {
            "type": "text",
            "id": "heading_line1",
            "label": "Heading Line 1",
            "default": "SUSTAINABILITY"
        },
        {
            "type": "text",
            "id": "heading_line2",
            "label": "Heading Line 2",
            "default": "FOR MODERN"
        },
        {
            "type": "text",
            "id": "heading_line3",
            "label": "Heading Line 3",
            "default": "CONSUMERS"
        },
        {
            "type": "textarea",
            "id": "hero_description",
            "label": "Hero Description",
            "default": "We specialize in crafting cutting-edge lifestyle experiences. Minimalist essentials meet dark innovation."
        },
        {
            "type": "image_picker",
            "id": "story_image",
            "label": "Brand Story Image"
        }
    ],
    "presets": [
        {
            "name": "Generations Studios - Full Theme"
        }
    ]
}
{% endschema %}
<!-- ==================== NAVIGATION ==================== -->
<nav class="fixed top-0 w-full bg-[#0a0a0a]/90 backdrop-blur-md border-b border-white/5 z-50 transition-all duration-300" id="navbar">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="flex justify-between items-center h-20">
            <!-- Logo -->
            <div class="flex-shrink-0 cursor-pointer" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">
                <a href="{{ routes.root_url }}" class="text-lg font-bold tracking-[0.2em] uppercase">
                    Generations<span class="font-light opacity-60">Studios</span>
                </a>
            </div>
            
            <!-- Desktop Menu -->
            <div class="hidden md:flex space-x-10">
                <a href="#home" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Home</a>
                <a href="#calendar" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Calendar</a>
                <a href="#lab" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Creative Lab</a>
                <a href="#shop" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Shop</a>
            </div>
            
            <!-- Icons -->
            <div class="flex items-center space-x-6">
                <button class="text-gray-400 hover:text-white transition-colors" onclick="toggleSearch()">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                </button>
                <button class="text-gray-400 hover:text-white transition-colors relative" onclick="toggleCart()">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg>
                    <span id="cart-badge" class="absolute -top-2 -right-2 bg-white text-black text-[10px] w-4 h-4 rounded-full flex items-center justify-center {% if cart.item_count == 0 %}hidden{% endif %} font-bold">{{ cart.item_count }}</span>
                </button>
                <button class="md:hidden text-gray-400 hover:text-white" onclick="toggleMobileMenu()">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 6h16M4 12h16M4 18h16"></path></svg>
                </button>
            </div>
        </div>
    </div>
    
    <!-- Mobile Menu -->
    <div id="mobile-menu" class="hidden md:hidden bg-[#0a0a0a] border-t border-white/5 animate-slide-in">
        <div class="px-6 py-6 space-y-4">
            <a href="#home" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Home</a>
            <a href="#calendar" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Calendar</a>
            <a href="#lab" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Creative Lab</a>
            <a href="#shop" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Shop</a>
        </div>
    </div>
</nav>

<!-- ==================== HERO SECTION ==================== -->
<section id="home" class="relative pt-20 min-h-screen flex items-center bg-[#0a0a0a] overflow-hidden">
    <div class="absolute inset-0 z-0">
        <div class="absolute inset-0 bg-gradient-to-b from-transparent via-[#0a0a0a]/50 to-[#0a0a0a]"></div>
        {% if section.settings.hero_image %}
            {{ section.settings.hero_image | image_url: width: 1920 | image_tag: class: 'w-full h-full object-cover opacity-40 grayscale', alt: 'Hero background' }}
        {% else %}
            <img src="https://images.unsplash.com/photo-1552374196-1ab2a1c593e8?w=1920&q=80" alt="Dark fashion" class="w-full h-full object-cover opacity-40 grayscale">
        {% endif %}
    </div>
    
    <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-8 py-32 w-full">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
            <div class="animate-fade-in">
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-6">Est. 2024</p>
                <h1 class="text-6xl md:text-8xl font-bold tracking-tighter mb-8 leading-[0.9]">
                    {{ section.settings.heading_line1 | default: 'SUSTAINABILITY' }}<br>
                    <span class="text-stroke">{{ section.settings.heading_line2 | default: 'FOR MODERN' }}</span><br>
                    {{ section.settings.heading_line3 | default: 'CONSUMERS' }}
                </h1>
                <p class="text-gray-400 text-lg mb-10 max-w-md leading-relaxed">
                    {{ section.settings.hero_description | default: 'We specialize in crafting cutting-edge lifestyle experiences. Minimalist essentials meet dark innovation.' }}
                </p>
                <div class="flex flex-col sm:flex-row gap-4">
                    <a href="#shop" class="btn-primary px-10 py-4 text-xs font-bold tracking-widest uppercase text-center inline-block">
                        Explore Collection
                    </a>
                    <a href="#calendar" class="btn-outline px-10 py-4 text-xs font-bold tracking-widest uppercase text-center inline-block">
                        View Calendar
                    </a>
                </div>
            </div>
            
            <div class="hidden lg:block relative">
                <div class="grid grid-cols-2 gap-4">
                    <div class="space-y-4 mt-12">
                        <div class="img-zoom aspect-[3/4] bg-[#111]">
                            <img src="https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 1">
                        </div>
                        <div class="img-zoom aspect-square bg-[#111]">
                            <img src="https://images.unsplash.com/photo-1503341504253-dff4815485f1?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 2">
                        </div>
                    </div>
                    <div class="space-y-4">
                        <div class="img-zoom aspect-square bg-[#111]">
                            <img src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 3">
                        </div>
                        <div class="img-zoom aspect-[3/4] bg-[#111]">
                            <img src="https://images.unsplash.com/photo-1509631179647-0177331693ae?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 4">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Scroll Indicator -->
    <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
        <svg class="w-6 h-6 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== BRAND STORY SECTION ==================== -->
<section class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
            <div class="order-2 lg:order-1">
                <div class="img-zoom aspect-[4/5] bg-[#111] relative">
                    {% if section.settings.story_image %}
                        {{ section.settings.story_image | image_url: width: 800 | image_tag: class: 'w-full h-full object-cover', alt: 'Brand story' }}
                    {% else %}
                        <img src="https://images.unsplash.com/photo-1558171813-4c088753af8f?w=800&q=80" class="w-full h-full object-cover" alt="Brand story">
                    {% endif %}
                    <div class="absolute bottom-6 left-6 bg-white text-black px-4 py-2 text-xs font-bold tracking-widest uppercase">
                        Since 2024
                    </div>
                </div>
            </div>
            <div class="order-1 lg:order-2">
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Our Philosophy</p>
                <h2 class="text-4xl md:text-6xl font-bold tracking-tighter mb-8">
                    UNVEILING EXCLUSIVE<br>
                    <span class="text-gray-500">STORY ABOUT</span><br>
                    OUR BRAND
                </h2>
                <p class="text-gray-400 leading-relaxed mb-8 max-w-lg">
                    Every piece is a narrative woven from sustainable materials and dark aesthetics. We don't follow trends—we engineer timeless essentials for the modern urban landscape.
                </p>
                <div class="flex items-center gap-8 text-xs tracking-widest uppercase text-gray-500">
                    <div>
                        <span class="block text-2xl font-bold text-white mb-1">50+</span>
                        AI Generated Drops
                    </div>
                    <div>
                        <span class="block text-2xl font-bold text-white mb-1">100%</span>
                        Sustainable
                    </div>
                    <div>
                        <span class="block text-2xl font-bold text-white mb-1">24h</span>
                        Global Shipping
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== DROP CALENDAR SECTION ==================== -->
<section id="calendar" class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="mb-20">
            <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Studio Schedule</p>
            <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">DROP CALENDAR</h2>
        </div>
        
        <div class="grid lg:grid-cols-3 gap-8">
            <!-- Calendar -->
            <div class="lg:col-span-1 bg-[#111] border border-white/5 p-8">
                <div class="flex justify-between items-center mb-8">
                    <h3 class="text-sm font-bold tracking-widest uppercase">February 2026</h3>
                    <div class="flex gap-2">
                        <button class="p-2 hover:bg-white/5 rounded transition-colors text-gray-400 hover:text-white" onclick="changeMonth(-1)">‹</button>
                        <button class="p-2 hover:bg-white/5 rounded transition-colors text-gray-400 hover:text-white" onclick="changeMonth(1)">›</button>
                    </div>
                </div>
                <div class="grid grid-cols-7 gap-1 text-center text-xs mb-4 text-gray-600 uppercase tracking-wider">
                    <div>Su</div><div>Mo</div><div>Tu</div><div>We</div><div>Th</div><div>Fr</div><div>Sa</div>
                </div>
                <div class="calendar-grid" id="calendar-grid"></div>
                <div class="mt-8 flex items-center gap-6 text-xs text-gray-500 uppercase tracking-wider">
                    <div class="flex items-center gap-2">
                        <div class="w-2 h-2 bg-white rounded-full"></div>
                        <span>Drop Day</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <div class="w-2 h-2 bg-gray-700 rounded-full"></div>
                        <span>Regular</span>
                    </div>
                </div>
            </div>
            
            <!-- Selected Drop Display -->
            <div class="lg:col-span-2">
                <div id="drop-display" class="h-full bg-[#111] border border-white/5 overflow-hidden relative group cursor-pointer">
                    <img id="drop-image" src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=1200&q=80" class="w-full h-full object-cover opacity-60 grayscale group-hover:grayscale-0 transition-all duration-700" alt="Drop preview">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent"></div>
                    <div class="absolute inset-0 p-10 flex flex-col justify-end">
                        <span class="inline-block px-3 py-1 bg-white text-black text-[10px] font-bold tracking-widest uppercase mb-4 w-fit">Upcoming Drop</span>
                        <h3 id="drop-title" class="text-3xl md:text-5xl font-bold tracking-tighter mb-4">Midnight Cotton Collection</h3>
                        <p id="drop-desc" class="text-gray-400 mb-6 max-w-lg text-sm leading-relaxed">AI-generated urban lifestyle photography featuring our heavyweight cotton essentials in monochromatic settings.</p>
                        <div class="flex items-center gap-6">
                            <span id="drop-date" class="text-sm tracking-widest uppercase text-gray-500">Feb 15, 2026</span>
                            <a href="#shop" class="px-8 py-3 bg-white text-black text-xs font-bold tracking-widest uppercase hover:bg-gray-200 transition-colors inline-block">
                                Preview
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== CREATIVE LAB SECTION ==================== -->
<section id="lab" class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="mb-20">
            <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Knowledge Base</p>
            <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">CREATIVE LAB</h2>
        </div>
        
        <!-- Tabs -->
        <div class="flex gap-8 mb-16 border-b border-white/10 pb-6 overflow-x-auto">
            <button onclick="switchTab('stories')" id="tab-stories" class="text-sm font-bold tracking-widest uppercase text-white whitespace-nowrap relative pb-6">
                Design Stories
                <span class="absolute bottom-0 left-0 w-full h-0.5 bg-white"></span>
            </button>
            <button onclick="switchTab('fabric')" id="tab-fabric" class="text-sm font-bold tracking-widest uppercase text-gray-500 hover:text-white transition-colors whitespace-nowrap relative pb-6">
                Fabric Education
            </button>
            <button onclick="switchTab('styling')" id="tab-styling" class="text-sm font-bold tracking-widest uppercase text-gray-500 hover:text-white transition-colors whitespace-nowrap relative pb-6">
                Styling Guides
            </button>
        </div>
        
        <!-- Tab Content: Design Stories -->
        <div class="tab-content active" id="content-stories">
            <div class="grid md:grid-cols-3 gap-6">
                <article class="product-card cursor-pointer group">
                    <div class="aspect-[4/3] overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1558171813-4c088753af8f?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Design process">
                    </div>
                    <div class="p-6">
                        <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Process</span>
                        <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">The Art of Minimalism</h3>
                        <p class="text-gray-400 text-sm leading-relaxed mb-4">How we strip away the unnecessary to focus on form, function, and timeless appeal.</p>
                        <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                            Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                        </span>
                    </div>
                </article>
                
                <article class="product-card cursor-pointer group">
                    <div class="aspect-[4/3] overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1441986300917-64674bd600d8?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Studio">
                    </div>
                    <div class="p-6">
                        <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Behind the Scenes</span>
                        <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">Studio Sessions</h3>
                        <p class="text-gray-400 text-sm leading-relaxed mb-4">A look inside our creative process, from initial sketches to final production.</p>
                        <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                            Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                        </span>
                    </div>
                </article>
                
                <article class="product-card cursor-pointer group">
                    <div class="aspect-[4/3] overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Sustainability">
                    </div>
                    <div class="p-6">
                        <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Sustainability</span>
                        <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">Zero Waste Journey</h3>
                        <p class="text-gray-400 text-sm leading-relaxed mb-4">Our commitment to eliminating waste through innovative pattern making.</p>
                        <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                            Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                        </span>
                    </div>
                </article>
            </div>
        </div>
        
        <!-- Tab Content: Fabric Education -->
        <div class="tab-content" id="content-fabric">
            <div class="grid md:grid-cols-2 gap-8">
                <div class="product-card p-8">
                    <h3 class="text-2xl font-bold mb-8 tracking-tight">Fabric Glossary</h3>
                    <div class="space-y-8">
                        <div class="flex gap-6 pb-8 border-b border-white/5">
                            <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🧵</div>
                            <div>
                                <h4 class="font-bold mb-2 tracking-tight">Organic Cotton</h4>
                                <p class="text-sm text-gray-400 leading-relaxed">Grown without synthetic pesticides, our organic cotton uses 91% less water than conventional cotton farming.</p>
                            </div>
                        </div>
                        <div class="flex gap-6 pb-8 border-b border-white/5">
                            <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🧶</div>
                            <div>
                                <h4 class="font-bold mb-2 tracking-tight">Recycled Fleece</h4>
                                <p class="text-sm text-gray-400 leading-relaxed">Made from post-consumer plastic bottles, transformed into ultra-soft fleece with superior warmth.</p>
                            </div>
                        </div>
                        <div class="flex gap-6">
                            <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🪡</div>
                            <div>
                                <h4 class="font-bold mb-2 tracking-tight">Tencel™ Modal</h4>
                                <p class="text-sm text-gray-400 leading-relaxed">Botanical fibers from sustainably harvested beech trees, known for exceptional breathability.</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="bg-gradient-to-br from-[#1a1a1a] to-[#0a0a0a] border border-white/5 p-8 relative overflow-hidden">
                    <div class="absolute top-0 right-0 w-64 h-64 bg-white/5 rounded-full blur-3xl"></div>
                    <div class="relative z-10">
                        <h3 class="text-2xl font-bold mb-8 tracking-tight">Quality Standards</h3>
                        <ul class="space-y-6">
                            <li class="flex items-start gap-4">
                                <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                <div>
                                    <span class="block font-bold mb-1">OEKO-TEX® Standard 100</span>
                                    <span class="text-sm text-gray-400">Certified free from harmful substances</span>
                                </div>
                            </li>
                            <li class="flex items-start gap-4">
                                <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                <div>
                                    <span class="block font-bold mb-1">GOTS Certified Organic</span>
                                    <span class="text-sm text-gray-400">Global Organic Textile Standard</span>
                                </div>
                            </li>
                            <li class="flex items-start gap-4">
                                <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                <div>
                                    <span class="block font-bold mb-1">Bluesign® Approved</span>
                                    <span class="text-sm text-gray-400">Sustainable chemical management</span>
                                </div>
                            </li>
                            <li class="flex items-start gap-4">
                                <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                <div>
                                    <span class="block font-bold mb-1">Fair Trade Certified™</span>
                                    <span class="text-sm text-gray-400">Ethical production standards</span>
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Tab Content: Styling Guides -->
        <div class="tab-content" id="content-styling">
            <div class="grid md:grid-cols-3 gap-6">
                <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                    <img src="https://images.unsplash.com/photo-1483985988355-763728e1935b?w=600&q=80" class="w-full h-full object-cover" alt="Styling 1">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                        <div class="absolute bottom-0 left-0 right-0 p-8">
                            <h4 class="font-bold text-xl tracking-tight mb-2">Monochrome Layers</h4>
                            <p class="text-sm text-gray-400">3 ways to style black & white</p>
                        </div>
                    </div>
                </div>
                <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                    <img src="https://images.unsplash.com/photo-1469334031218-e382a71b716b?w=600&q=80" class="w-full h-full object-cover" alt="Styling 2">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                        <div class="absolute bottom-0 left-0 right-0 p-8">
                            <h4 class="font-bold text-xl tracking-tight mb-2">Essential Basics</h4>
                            <p class="text-sm text-gray-400">Building a capsule wardrobe</p>
                        </div>
                    </div>
                </div>
                <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                    <img src="https://images.unsplash.com/photo-1445205170230-053b83016050?w=600&q=80" class="w-full h-full object-cover" alt="Styling 3">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                        <div class="absolute bottom-0 left-0 right-0 p-8">
                            <h4 class="font-bold text-xl tracking-tight mb-2">Street Style</h4>
                            <p class="text-sm text-gray-400">Urban minimalism guide</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== SHOP SECTION ==================== -->
<section id="shop" class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="flex flex-col md:flex-row md:items-end md:justify-between mb-20 gap-8">
            <div>
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Collection</p>
                <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">OUR BESTSELLER</h2>
            </div>
            
            <!-- Category Filter -->
            <div class="flex gap-4 flex-wrap">
                <button onclick="filterProducts('all')" class="filter-btn active px-6 py-3 bg-white text-black text-xs font-bold tracking-widest uppercase transition-all" data-filter="all">All</button>
                <button onclick="filterProducts('hoodies')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="hoodies">Hoodies</button>
                <button onclick="filterProducts('tshirts')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="tshirts">T-Shirts</button>
                <button onclick="filterProducts('posters')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="posters">Silver Posters</button>
            </div>
        </div>
        
        <!-- Products Grid -->
        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6" id="products-grid">
            {% for product in collections.all.products limit: 8 %}
                <div class="product-card group cursor-pointer animate-fade-in" data-category="{{ product.type | handle | default: 'all' }}">
                    <div class="aspect-[4/5] overflow-hidden relative bg-[#111]">
                        {% if product.featured_image %}
                            {{ product.featured_image | image_url: width: 600 | image_tag: class: 'w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105', alt: product.title }}
                        {% else %}
                            <img src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=600&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="{{ product.title }}">
                        {% endif %}
                        
                        {% if product.available %}
                            <button onclick="addToCart({{ product.variants.first.id }})" class="absolute bottom-4 right-4 w-12 h-12 bg-white text-black rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transform translate-y-2 group-hover:translate-y-0 transition-all duration-300 hover:bg-gray-200">
                                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                            </button>
                        {% endif %}
                        
                        {% if product.tags contains 'Limited' %}
                            <span class="absolute top-4 left-4 px-3 py-1 bg-white text-black text-[10px] font-bold tracking-widest uppercase">Limited</span>
                        {% endif %}
                        
                        {% unless product.available %}
                            <span class="absolute top-4 left-4 px-3 py-1 bg-gray-800 text-white text-[10px] font-bold tracking-widest uppercase">Sold Out</span>
                        {% endunless %}
                    </div>
                    <div class="p-6">
                        <h3 class="font-bold text-sm mb-2 tracking-tight group-hover:text-gray-300 transition-colors">{{ product.title }}</h3>
                        <p class="text-gray-500 text-xs mb-3 line-clamp-1">{{ product.description | strip_html | truncate: 60 }}</p>
                        <p class="font-bold text-sm">{{ product.price | money }}</p>
                    </div>
                </div>
            {% endfor %}
        </div>
    </div>
</section>

<div class="section-divider max-w-7xl mx-auto"></div>

<!-- ==================== SERVICES SECTION ==================== -->
<section class="py-32 bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
            <div>
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">What We Offer</p>
                <h2 class="text-4xl md:text-5xl font-bold tracking-tighter mb-12">OUR SERVICES</h2>
                
                <div class="space-y-8">
                    <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                        <div class="flex items-center gap-4">
                            <span class="text-gray-500 text-sm">01</span>
                            <span class="font-bold tracking-wide">Global Shipping</span>
                        </div>
                        <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                    </div>
                    <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                        <div class="flex items-center gap-4">
                            <span class="text-gray-500 text-sm">02</span>
                            <span class="font-bold tracking-wide">AI Design Consultation</span>
                        </div>
                        <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                    </div>
                    <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                        <div class="flex items-center gap-4">
                            <span class="text-gray-500 text-sm">03</span>
                            <span class="font-bold tracking-wide">Custom Branding</span>
                        </div>
                        <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                    </div>
                    <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                        <div class="flex items-center gap-4">
                            <span class="text-gray-500 text-sm">04</span>
                            <span class="font-bold tracking-wide">24/7 Support</span>
                        </div>
                        <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                    </div>
                </div>
            </div>
            
            <div class="relative">
                <div class="img-zoom aspect-[4/5] bg-[#111]">
                    <img src="https://images.unsplash.com/photo-1552374196-1ab2a1c593e8?w=800&q=80" class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700" alt="Services">
                </div>
                <div class="absolute -bottom-6 -left-6 bg-white text-black p-6 max-w-xs">
                    <p class="text-xs font-bold tracking-widest uppercase mb-2">Premium Service</p>
                    <p class="text-sm font-medium">White-glove treatment for every order, from studio to doorstep.</p>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- ==================== NEWSLETTER SECTION ==================== -->
<section class="py-32 bg-[#111] border-y border-white/5">
    <div class="max-w-4xl mx-auto px-6 lg:px-8 text-center">
        <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Stay Updated</p>
        <h2 class="text-3xl md:text-5xl font-bold tracking-tighter mb-8">JOIN THE NEWSLETTER</h2>
        <p class="text-gray-400 mb-10 max-w-lg mx-auto">Be the first to know about exclusive drops, AI-generated collections, and member-only events.</p>
        
        {% form 'customer', class: 'flex flex-col sm:flex-row gap-4 max-w-md mx-auto' %}
            <input 
                type="email" 
                name="contact[email]" 
                placeholder="Enter your email" 
                class="flex-1 px-6 py-4 bg-[#0a0a0a] border border-white/10 text-white placeholder-gray-600 focus:outline-none focus:border-white/30 transition-colors text-sm"
                required
            >
            <button type="submit" class="px-8 py-4 bg-white text-black font-bold text-xs tracking-widest uppercase hover:bg-gray-200 transition-colors">
                Subscribe
            </button>
        {% endform %}
    </div>
</section>

<!-- ==================== FOOTER ==================== -->
<footer class="bg-[#0a0a0a] pt-20 pb-10">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="grid md:grid-cols-4 gap-12 mb-20">
            <div class="md:col-span-2">
                <h3 class="text-lg font-bold tracking-[0.2em] uppercase mb-6">
                    Generations<span class="font-light opacity-60">Studios</span>
                </h3>
                <p class="text-gray-500 text-sm leading-relaxed max-w-sm mb-8">
                    Crafting cutting-edge lifestyle apparel for the modern consumer. Sustainable, minimal, timeless.
                </p>
                <div class="flex gap-4">
                    <a href="#" class="w-10 h-10 border border-white/10 flex items-center justify-center hover:border-white hover:bg-white hover:text-black transition-all">
                        <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/></svg>
                    </a>
                    <a href="#" class="w-10 h-10 border border-white/10 flex items-center justify-center hover:border-white hover:bg-white hover:text-black transition-all">
                        <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
                    </a>
                </div>
            </div>
            <div>
                <h4 class="font-bold text-xs tracking-widest uppercase mb-6 text-gray-400">Shop</h4>
                <ul class="space-y-4 text-sm text-gray-500">
                    <li><a href="#shop" class="hover:text-white transition-colors">New Arrivals</a></li>
                    <li><a href="#shop" class="hover:text-white transition-colors">Best Sellers</a></li>
                    <li><a href="#shop" class="hover:text-white transition-colors">Hoodies</a></li>
                    <li><a href="#shop" class="hover:text-white transition-colors">T-Shirts</a></li>
                    <li><a href="#shop" class="hover:text-white transition-colors">Posters</a></li>
                </ul>
            </div>
            <div>
                <h4 class="font-bold text-xs tracking-widest uppercase mb-6 text-gray-400">Support</h4>
                <ul class="space-y-4 text-sm text-gray-500">
                    <li><a href="#" class="hover:text-white transition-colors">Contact</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Shipping</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Returns</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Size Guide</a></li>
                </ul>
            </div>
        </div>
        
        <div class="border-t border-white/10 pt-8 flex flex-col md:flex-row justify-between items-center gap-4">
            <p class="text-xs text-gray-600">© {{ 'now' | date: '%Y' }} Generations Studios. All rights reserved.</p>
            <div class="flex gap-8 text-xs text-gray-600">
                <a href="#" class="hover:text-white transition-colors">Terms</a>
                <a href="#" class="hover:text-white transition-colors">Privacy</a>
                <a href="#" class="hover:text-white transition-colors">Cookies</a>
            </div>
        </div>
    </div>
</footer>

<!-- ==================== CART SIDEBAR ==================== -->
<div id="cart-sidebar" class="fixed inset-y-0 right-0 w-full md:w-[480px] bg-[#0a0a0a] border-l border-white/10 transform translate-x-full transition-transform duration-500 z-50 flex flex-col">
    <div class="p-8 border-b border-white/10 flex justify-between items-center">
        <h2 class="text-sm font-bold tracking-widest uppercase">Shopping Cart</h2>
        <button onclick="toggleCart()" class="p-2 hover:bg-white/5 rounded-full transition-colors">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
        </button>
    </div>
    
    <div class="flex-1 overflow-y-auto p-8" id="cart-items">
        {% if cart.item_count == 0 %}
            <div class="text-center text-gray-600 mt-20">
                <div class="text-4xl mb-4 opacity-20">🛒</div>
                <p class="text-sm tracking-widest uppercase mb-4">Your cart is empty</p>
                <button onclick="toggleCart(); window.location.href='#shop'" class="text-xs font-bold tracking-widest uppercase text-white hover:text-gray-300 transition-colors border-b border-white/30 pb-1">
                    Start Shopping
                </button>
            </div>
        {% else %}
            {% for item in cart.items %}
                <div class="flex gap-6 mb-8 animate-fade-in">
                    <div class="w-24 h-24 bg-[#111] overflow-hidden flex-shrink-0">
                        {% if item.image %}
                            {{ item.image | image_url: width: 200 | image_tag: class: 'w-full h-full object-cover grayscale', alt: item.title }}
                        {% endif %}
                    </div>
                    <div class="flex-1 flex flex-col justify-between">
                        <div>
                            <h4 class="font-bold text-sm mb-1 tracking-tight">{{ item.product.title }}</h4>
                            <p class="text-gray-500 text-xs">{{ item.price | money }}</p>
                        </div>
                        <div class="flex items-center justify-between">
                            <div class="flex items-center gap-4 border border-white/10 px-4 py-2">
                                <button onclick="updateCartItem({{ item.variant_id }}, {{ item.quantity | minus: 1 }})" class="text-gray-500 hover:text-white transition-colors">−</button>
                                <span class="text-sm font-bold w-4 text-center">{{ item.quantity }}</span>
                                <button onclick="updateCartItem({{ item.variant_id }}, {{ item.quantity | plus: 1 }})" class="text-gray-500 hover:text-white transition-colors">+</button>
                            </div>
                            <button onclick="removeCartItem({{ item.variant_id }})" class="text-gray-600 hover:text-white transition-colors text-xs tracking-widest uppercase">
                                Remove
                            </button>
                        </div>
                    </div>
                </div>
            {% endfor %}
        {% endif %}
    </div>
    
    {% if cart.item_count > 0 %}
    <div class="border-t border-white/10 p-8 bg-[#111]">
        <div class="flex justify-between mb-4 text-sm">
            <span class="text-gray-500 uppercase tracking-wider text-xs">Subtotal</span>
            <span class="font-bold">{{ cart.total_price | money }}</span>
        </div>
        <div class="flex justify-between mb-8 text-sm">
            <span class="text-gray-500 uppercase tracking-wider text-xs">Shipping</span>
            <span class="text-gray-400 text-xs">Calculated at checkout</span>
        </div>
        <div class="flex justify-between mb-8 text-lg font-bold">
            <span class="tracking-tight">Total</span>
            <span>{{ cart.total_price | money }}</span>
        </div>
        <a href="{{ routes.cart_url }}" class="block w-full py-4 bg-white text-black font-bold text-xs tracking-widest uppercase hover:bg-gray-200 transition-all text-center">
            Checkout
        </a>
    </div>
    {% endif %}
</div>

<!-- Overlay -->
<div id="overlay" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-40 hidden opacity-0 transition-opacity duration-500" onclick="toggleCart()"></div>

<!-- ==================== SEARCH MODAL ==================== -->
<div id="search-modal" class="fixed inset-0 bg-[#0a0a0a]/98 backdrop-blur-md z-50 hidden flex items-center justify-center p-6">
    <button onclick="toggleSearch()" class="absolute top-8 right-8 p-2 hover:bg-white/5 rounded-full transition-colors">
        <svg class="w-8 h-8 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
    </button>
    <div class="w-full max-w-3xl">
        <form action="{{ routes.search_url }}" method="get" role="search" class="w-full">
            <input 
                type="search" 
                name="q" 
                placeholder="Search products..." 
                class="w-full text-5xl md:text-7xl font-bold bg-transparent border-b-2 border-white/20 pb-6 focus:outline-none focus:border-white placeholder-gray-800 text-center"
            >
        </form>
        <p class="mt-8 text-center text-gray-500 text-xs tracking-widest uppercase">Press Enter to search</p>
    </div>
</div>

<!-- ==================== JAVASCRIPT ==================== -->
<script>
    // Global Variables
    window.shopUrl = '{{ shop.url }}';
    window.routes = {
        cart_add_url: '{{ routes.cart_add_url }}',
        cart_change_url: '{{ routes.cart_change_url }}',
        cart_update_url: '{{ routes.cart_update_url }}',
        cart_url: '{{ routes.cart_url }}',
        predictive_search_url: '{{ routes.predictive_search_url }}'
    };

    // ==================== NAVIGATION ====================
    function toggleMobileMenu() {
        document.getElementById('mobile-menu').classList.toggle('hidden');
    }

    function toggleSearch() {
        const modal = document.getElementById('search-modal');
        modal.classList.toggle('hidden');
        if (!modal.classList.contains('hidden')) {
            modal.querySelector('input').focus();
        }
    }

    function toggleCart() {
        const sidebar = document.getElementById('cart-sidebar');
        const overlay = document.getElementById('overlay');
        
        if (sidebar.classList.contains('translate-x-full')) {
            sidebar.classList.remove('translate-x-full');
            sidebar.classList.add('translate-x-0');
            overlay.classList.remove('hidden');
            setTimeout(() => overlay.classList.remove('opacity-0'), 10);
            document.body.style.overflow = 'hidden';
        } else {
            sidebar.classList.add('translate-x-full');
            sidebar.classList.remove('translate-x-0');
            overlay.classList.add('opacity-0');
            setTimeout(() => overlay.classList.add('hidden'), 500);
            document.body.style.overflow = '';
        }
    }

    // Navbar scroll effect
    window.addEventListener('scroll', () => {
        const navbar = document.getElementById('navbar');
        if (window.scrollY > 50) {
            navbar.classList.add('bg-[#0a0a0a]/95');
        } else {
            navbar.classList.remove('bg-[#0a0a0a]/95');
        }
    });

    // ==================== CALENDAR ====================
    function generateCalendar() {
        const grid = document.getElementById('calendar-grid');
        const daysInMonth = 28;
        const startDay = 0;
        
        let html = '';
        for (let i = 0; i < startDay; i++) {
            html += '<div class="calendar-day text-gray-800"></div>';
        }
        
        const dropDays = [5, 12, 15, 19, 26];
        for (let i = 1; i <= daysInMonth; i++) {
            const hasDrop = dropDays.includes(i);
            const isSelected = i === 15;
            html += `<div class="calendar-day ${hasDrop ? 'has-drop' : ''} ${isSelected ? 'selected' : ''}" onclick="selectDate(${i})">${i}</div>`;
        }
        
        grid.innerHTML = html;
    }

    function selectDate(day) {
        document.querySelectorAll('.calendar-day').forEach(d => d.classList.remove('selected'));
        event.target.classList.add('selected');
        
        const titles = ['Urban Shadows', 'Midnight Cotton', 'Silver Linings', 'Monochrome Dreams', 'Essential Basics'];
        const images = [
            'https://images.unsplash.com/photo-1503341504253-dff4815485f1?w=1200&q=80',
            'https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=1200&q=80',
            'https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?w=1200&q=80',
            'https://images.unsplash.com/photo-1509631179647-0177331693ae?w=1200&q=80',
            'https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=1200&q=80'
        ];
        
        const index = (day % 5);
        document.getElementById('drop-title').textContent = titles[index] + ' Collection';
        document.getElementById('drop-image').src = images[index];
        document.getElementById('drop-date').textContent = `Feb ${day}, 2026`;
    }

    function changeMonth(delta) {
        const grid = document.getElementById('calendar-grid');
        grid.style.opacity = '0';
        setTimeout(() => {
            generateCalendar();
            grid.style.opacity = '1';
        }, 200);
    }

    // ==================== TABS ====================
    function switchTab(tab) {
        document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
        document.getElementById(`content-${tab}`).classList.add('active');
        
        ['stories', 'fabric', 'styling'].forEach(t => {
            const btn = document.getElementById(`tab-${t}`);
            const indicator = btn.querySelector('span') || document.createElement('span');
            
            if (t === tab) {
                btn.classList.remove('text-gray-500');
                btn.classList.add('text-white');
                if (!btn.querySelector('span')) {
                    indicator.className = 'absolute bottom-0 left-0 w-full h-0.5 bg-white';
                    btn.appendChild(indicator);
                }
            } else {
                btn.classList.add('text-gray-500');
                btn.classList.remove('text-white');
                const existingIndicator = btn.querySelector('span');
                if (existingIndicator) existingIndicator.remove();
            }
        });
    }

    // ==================== PRODUCT FILTER ====================
    function filterProducts(category) {
        const products = document.querySelectorAll('#products-grid > div');
        
        document.querySelectorAll('.filter-btn').forEach(btn => {
            if (btn.dataset.filter === category) {
                btn.classList.add('bg-white', 'text-black', 'border-white');
                btn.classList.remove('text-gray-400', 'border-white/20');
            } else {
                btn.classList.remove('bg-white', 'text-black', 'border-white');
                btn.classList.add('text-gray-400', 'border-white/20');
            }
        });
        
        products.forEach(product => {
            if (category === 'all' || product.dataset.category === category) {
                product.style.display = 'block';
            } else {
                product.style.display = 'none';
            }
        });
    }

    // ==================== CART FUNCTIONS ====================
    async function addToCart(variantId) {
        const formData = {
            'items': [{
                'id': variantId,
                'quantity': 1
            }]
        };
        
        try {
            const response = await fetch(window.routes.cart_add_url, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(formData)
            });
            
            if (response.ok) {
                const cartData = await response.json();
                updateCartUI(cartData);
                toggleCart();
                
                // Animate badge
                const badge = document.getElementById('cart-badge');
                badge.classList.add('cart-bounce');
                setTimeout(() => badge.classList.remove('cart-bounce'), 300);
            }
        } catch (error) {
            console.error('Error adding to cart:', error);
        }
    }

    async function updateCartItem(variantId, quantity) {
        if (quantity < 1) {
            await removeCartItem(variantId);
            return;
        }
        
        try {
            const response = await fetch(window.routes.cart_change_url, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ id: variantId, quantity: quantity })
            });
            
            if (response.ok) {
                window.location.reload();
            }
        } catch (error) {
            console.error('Error updating cart:', error);
        }
    }

    async function removeCartItem(variantId) {
        await updateCartItem(variantId, 0);
    }

    function updateCartUI(cartData) {
        // Refresh the page to show updated cart
        window.location.reload();
    }

    // ==================== INITIALIZATION ====================
    document.addEventListener('DOMContentLoaded', () => {
        generateCalendar();
        
        // Smooth scroll for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });
    });
</script>

{% schema %}
{
    "name": "Generations Studios - Full Theme",
    "settings": [
        {
            "type": "image_picker",
            "id": "hero_image",
            "label": "Hero Background Image"
        },
        {
            "type": "text",
            "id": "heading_line1",
            "label": "Heading Line 1",
            "default": "SUSTAINABILITY"
        },
        {
            "type": "text",
            "id": "heading_line2",
            "label": "Heading Line 2",
            "default": "FOR MODERN"
        },
        {
            "type": "text",
            "id": "heading_line3",
            "label": "Heading Line 3",
            "default": "CONSUMERS"
        },
        {
            "type": "textarea",
            "id": "hero_description",
            "label": "Hero Description",
            "default": "We specialize in crafting cutting-edge lifestyle experiences. Minimalist essentials meet dark innovation."
        },
        {
            "type": "image_picker",
            "id": "story_image",
            "label": "Brand Story Image"
        }
    ],
    "presets": [
        {
            "name": "Generations Studios - Full Theme"
        }
    ]
}
{% endschema %}
        
        /* Text Stroke Effect */
        .text-stroke {
            -webkit-text-stroke: 1px rgba(255,255,255,0.3);
            color: transparent;
        }
        
        /* Gradient Text */
        .gradient-text {
            background: linear-gradient(135deg, #fff 0%, #888 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        /* Custom Button Styles */
        .btn-primary {
            background: #fff;
            color: #000;
            transition: all 0.3s ease;
        }
        .btn-primary:hover {
            background: #e0e0e0;
            transform: translateY(-2px);
        }
        
        .btn-outline {
            border: 1px solid rgba(255,255,255,0.3);
            color: #fff;
            transition: all 0.3s ease;
        }
        .btn-outline:hover {
            border-color: #fff;
            background: rgba(255,255,255,0.05);
        }
        
        /* Section Divider */
        .section-divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
        }
        
        /* Product Card */
        .product-card {
            background: #111;
            border: 1px solid rgba(255,255,255,0.05);
            transition: all 0.4s ease;
        }
        .product-card:hover {
            border-color: rgba(255,255,255,0.2);
            background: #1a1a1a;
        }
        
        /* Nav Link Underline */
        .nav-link {
            position: relative;
        }
        .nav-link::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 0;
            width: 0;
            height: 1px;
            background: #fff;
            transition: width 0.3s ease;
        }
        .nav-link:hover::after {
            width: 100%;
        }
    </style>
</head>
<body class="antialiased selection:bg-white selection:text-black">

    <!-- Noise Overlay -->
    <div class="noise-overlay"></div>

    <!-- Navigation -->
    <nav class="fixed top-0 w-full bg-[#0a0a0a]/90 backdrop-blur-md border-b border-white/5 z-50 transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <!-- Logo -->
                <div class="flex-shrink-0 cursor-pointer" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">
                    <h1 class="text-lg font-bold tracking-[0.2em] uppercase">
                        Generations<span class="font-light opacity-60">Studios</span>
                    </h1>
                </div>
                
                <!-- Desktop Menu -->
                <div class="hidden md:flex space-x-10">
                    <a href="#home" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Home</a>
                    <a href="#calendar" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Calendar</a>
                    <a href="#lab" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Creative Lab</a>
                    <a href="#shop" class="nav-link text-xs font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Shop</a>
                </div>
                
                <!-- Icons -->
                <div class="flex items-center space-x-6">
                    <button class="text-gray-400 hover:text-white transition-colors" onclick="toggleSearch()">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                    </button>
                    <button class="text-gray-400 hover:text-white transition-colors relative" onclick="toggleCart()">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg>
                        <span id="cart-badge" class="absolute -top-2 -right-2 bg-white text-black text-[10px] w-4 h-4 rounded-full flex items-center justify-center hidden font-bold">0</span>
                    </button>
                    <button class="md:hidden text-gray-400 hover:text-white" onclick="toggleMobileMenu()">
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 6h16M4 12h16M4 18h16"></path></svg>
                    </button>
                </div>
            </div>
        </div>
        
        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-[#0a0a0a] border-t border-white/5 animate-slide-in">
            <div class="px-6 py-6 space-y-4">
                <a href="#home" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Home</a>
                <a href="#calendar" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Calendar</a>
                <a href="#lab" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Creative Lab</a>
                <a href="#shop" class="block text-sm font-medium tracking-widest uppercase text-gray-400 hover:text-white transition-colors">Shop</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="relative pt-20 min-h-screen flex items-center bg-[#0a0a0a] overflow-hidden">
        <div class="absolute inset-0 z-0">
            <div class="absolute inset-0 bg-gradient-to-b from-transparent via-[#0a0a0a]/50 to-[#0a0a0a]"></div>
            <img src="https://images.unsplash.com/photo-1552374196-1ab2a1c593e8?w=1920&q=80" alt="Dark fashion" class="w-full h-full object-cover opacity-40 grayscale">
        </div>
        
        <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-8 py-32 w-full">
            <div class="grid lg:grid-cols-2 gap-16 items-center">
                <div class="animate-fade-in">
                    <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-6">Est. 2024</p>
                    <h1 class="text-6xl md:text-8xl font-bold tracking-tighter mb-8 leading-[0.9]">
                        SUSTAINABILITY<br>
                        <span class="text-stroke">FOR MODERN</span><br>
                        CONSUMERS
                    </h1>
                    <p class="text-gray-400 text-lg mb-10 max-w-md leading-relaxed">
                        We specialize in crafting cutting-edge lifestyle experiences. Minimalist essentials meet dark innovation.
                    </p>
                    <div class="flex flex-col sm:flex-row gap-4">
                        <button onclick="scrollToSection('shop')" class="btn-primary px-10 py-4 text-xs font-bold tracking-widest uppercase">
                            Explore Collection
                        </button>
                        <button onclick="scrollToSection('calendar')" class="btn-outline px-10 py-4 text-xs font-bold tracking-widest uppercase">
                            View Calendar
                        </button>
                    </div>
                </div>
                
                <div class="hidden lg:block relative">
                    <div class="grid grid-cols-2 gap-4">
                        <div class="space-y-4 mt-12">
                            <div class="img-zoom aspect-[3/4] bg-[#111]">
                                <img src="https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 1">
                            </div>
                            <div class="img-zoom aspect-square bg-[#111]">
                                <img src="https://images.unsplash.com/photo-1503341504253-dff4815485f1?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 2">
                            </div>
                        </div>
                        <div class="space-y-4">
                            <div class="img-zoom aspect-square bg-[#111]">
                                <img src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 3">
                            </div>
                            <div class="img-zoom aspect-[3/4] bg-[#111]">
                                <img src="https://images.unsplash.com/photo-1509631179647-0177331693ae?w=600&q=80" class="w-full h-full object-cover" alt="Fashion 4">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Scroll Indicator -->
        <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
            <svg class="w-6 h-6 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
        </div>
    </section>

    <div class="section-divider max-w-7xl mx-auto"></div>

    <!-- Brand Story Section -->
    <section class="py-32 bg-[#0a0a0a]">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="grid lg:grid-cols-2 gap-16 items-center">
                <div class="order-2 lg:order-1">
                    <div class="img-zoom aspect-[4/5] bg-[#111] relative">
                        <img src="https://images.unsplash.com/photo-1558171813-4c088753af8f?w=800&q=80" class="w-full h-full object-cover" alt="Brand story">
                        <div class="absolute bottom-6 left-6 bg-white text-black px-4 py-2 text-xs font-bold tracking-widest uppercase">
                            Since 2024
                        </div>
                    </div>
                </div>
                <div class="order-1 lg:order-2">
                    <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Our Philosophy</p>
                    <h2 class="text-4xl md:text-6xl font-bold tracking-tighter mb-8">
                        UNVEILING EXCLUSIVE<br>
                        <span class="text-gray-500">STORY ABOUT</span><br>
                        OUR BRAND
                    </h2>
                    <p class="text-gray-400 leading-relaxed mb-8 max-w-lg">
                        Every piece is a narrative woven from sustainable materials and dark aesthetics. We don't follow trends—we engineer timeless essentials for the modern urban landscape.
                    </p>
                    <div class="flex items-center gap-8 text-xs tracking-widest uppercase text-gray-500">
                        <div>
                            <span class="block text-2xl font-bold text-white mb-1">50+</span>
                            AI Generated Drops
                        </div>
                        <div>
                            <span class="block text-2xl font-bold text-white mb-1">100%</span>
                            Sustainable
                        </div>
                        <div>
                            <span class="block text-2xl font-bold text-white mb-1">24h</span>
                            Global Shipping
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-7xl mx-auto"></div>

    <!-- Photo Calendar Section -->
    <section id="calendar" class="py-32 bg-[#0a0a0a]">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="mb-20">
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Studio Schedule</p>
                <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">DROP CALENDAR</h2>
            </div>
            
            <div class="grid lg:grid-cols-3 gap-8">
                <!-- Calendar -->
                <div class="lg:col-span-1 bg-[#111] border border-white/5 p-8">
                    <div class="flex justify-between items-center mb-8">
                        <h3 class="text-sm font-bold tracking-widest uppercase">February 2026</h3>
                        <div class="flex gap-2">
                            <button class="p-2 hover:bg-white/5 rounded transition-colors text-gray-400 hover:text-white" onclick="changeMonth(-1)">‹</button>
                            <button class="p-2 hover:bg-white/5 rounded transition-colors text-gray-400 hover:text-white" onclick="changeMonth(1)">›</button>
                        </div>
                    </div>
                    <div class="grid grid-cols-7 gap-1 text-center text-xs mb-4 text-gray-600 uppercase tracking-wider">
                        <div>Su</div><div>Mo</div><div>Tu</div><div>We</div><div>Th</div><div>Fr</div><div>Sa</div>
                    </div>
                    <div class="calendar-grid" id="calendar-grid"></div>
                    <div class="mt-8 flex items-center gap-6 text-xs text-gray-500 uppercase tracking-wider">
                        <div class="flex items-center gap-2">
                            <div class="w-2 h-2 bg-white rounded-full"></div>
                            <span>Drop Day</span>
                        </div>
                        <div class="flex items-center gap-2">
                            <div class="w-2 h-2 bg-gray-700 rounded-full"></div>
                            <span>Regular</span>
                        </div>
                    </div>
                </div>
                
                <!-- Selected Drop Display -->
                <div class="lg:col-span-2">
                    <div id="drop-display" class="h-full bg-[#111] border border-white/5 overflow-hidden relative group cursor-pointer">
                        <img id="drop-image" src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=1200&q=80" class="w-full h-full object-cover opacity-60 grayscale group-hover:grayscale-0 transition-all duration-700" alt="Drop preview">
                        <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent"></div>
                        <div class="absolute inset-0 p-10 flex flex-col justify-end">
                            <span class="inline-block px-3 py-1 bg-white text-black text-[10px] font-bold tracking-widest uppercase mb-4 w-fit">Upcoming Drop</span>
                            <h3 id="drop-title" class="text-3xl md:text-5xl font-bold tracking-tighter mb-4">Midnight Cotton Collection</h3>
                            <p id="drop-desc" class="text-gray-400 mb-6 max-w-lg text-sm leading-relaxed">AI-generated urban lifestyle photography featuring our heavyweight cotton essentials in monochromatic settings.</p>
                            <div class="flex items-center gap-6">
                                <span id="drop-date" class="text-sm tracking-widest uppercase text-gray-500">Feb 15, 2026</span>
                                <button class="px-8 py-3 bg-white text-black text-xs font-bold tracking-widest uppercase hover:bg-gray-200 transition-colors">
                                    Preview
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-7xl mx-auto"></div>

    <!-- Creative Lab Section -->
    <section id="lab" class="py-32 bg-[#0a0a0a]">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="mb-20">
                <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Knowledge Base</p>
                <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">CREATIVE LAB</h2>
            </div>
            
            <!-- Tabs -->
            <div class="flex gap-8 mb-16 border-b border-white/10 pb-6 overflow-x-auto">
                <button onclick="switchTab('stories')" id="tab-stories" class="text-sm font-bold tracking-widest uppercase text-white whitespace-nowrap relative pb-6">
                    Design Stories
                    <span class="absolute bottom-0 left-0 w-full h-0.5 bg-white"></span>
                </button>
                <button onclick="switchTab('fabric')" id="tab-fabric" class="text-sm font-bold tracking-widest uppercase text-gray-500 hover:text-white transition-colors whitespace-nowrap relative pb-6">
                    Fabric Education
                </button>
                <button onclick="switchTab('styling')" id="tab-styling" class="text-sm font-bold tracking-widest uppercase text-gray-500 hover:text-white transition-colors whitespace-nowrap relative pb-6">
                    Styling Guides
                </button>
            </div>
            
            <!-- Tab Content -->
            <div class="tab-content active" id="content-stories">
                <div class="grid md:grid-cols-3 gap-6">
                    <article class="product-card cursor-pointer group">
                        <div class="aspect-[4/3] overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1558171813-4c088753af8f?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Design process">
                        </div>
                        <div class="p-6">
                            <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Process</span>
                            <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">The Art of Minimalism</h3>
                            <p class="text-gray-400 text-sm leading-relaxed mb-4">How we strip away the unnecessary to focus on form, function, and timeless appeal.</p>
                            <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                                Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                            </span>
                        </div>
                    </article>
                    
                    <article class="product-card cursor-pointer group">
                        <div class="aspect-[4/3] overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1441986300917-64674bd600d8?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Studio">
                        </div>
                        <div class="p-6">
                            <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Behind the Scenes</span>
                            <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">Studio Sessions</h3>
                            <p class="text-gray-400 text-sm leading-relaxed mb-4">A look inside our creative process, from initial sketches to final production.</p>
                            <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                                Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                            </span>
                        </div>
                    </article>
                    
                    <article class="product-card cursor-pointer group">
                        <div class="aspect-[4/3] overflow-hidden">
                            <img src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=800&q=80" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105" alt="Sustainability">
                        </div>
                        <div class="p-6">
                            <span class="text-[10px] font-bold tracking-widest uppercase text-gray-500">Sustainability</span>
                            <h3 class="text-lg font-bold mt-2 mb-3 tracking-tight">Zero Waste Journey</h3>
                            <p class="text-gray-400 text-sm leading-relaxed mb-4">Our commitment to eliminating waste through innovative pattern making.</p>
                            <span class="text-xs font-bold tracking-widest uppercase text-white group-hover:text-gray-300 transition-colors flex items-center gap-2">
                                Read More <span class="group-hover:translate-x-1 transition-transform">→</span>
                            </span>
                        </div>
                    </article>
                </div>
            </div>
            
            <div class="tab-content" id="content-fabric">
                <div class="grid md:grid-cols-2 gap-8">
                    <div class="product-card p-8">
                        <h3 class="text-2xl font-bold mb-8 tracking-tight">Fabric Glossary</h3>
                        <div class="space-y-8">
                            <div class="flex gap-6 pb-8 border-b border-white/5">
                                <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🧵</div>
                                <div>
                                    <h4 class="font-bold mb-2 tracking-tight">Organic Cotton</h4>
                                    <p class="text-sm text-gray-400 leading-relaxed">Grown without synthetic pesticides, our organic cotton uses 91% less water than conventional cotton farming.</p>
                                </div>
                            </div>
                            <div class="flex gap-6 pb-8 border-b border-white/5">
                                <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🧶</div>
                                <div>
                                    <h4 class="font-bold mb-2 tracking-tight">Recycled Fleece</h4>
                                    <p class="text-sm text-gray-400 leading-relaxed">Made from post-consumer plastic bottles, transformed into ultra-soft fleece with superior warmth.</p>
                                </div>
                            </div>
                            <div class="flex gap-6">
                                <div class="w-16 h-16 bg-[#0a0a0a] border border-white/10 flex items-center justify-center text-2xl flex-shrink-0">🪡</div>
                                <div>
                                    <h4 class="font-bold mb-2 tracking-tight">Tencel™ Modal</h4>
                                    <p class="text-sm text-gray-400 leading-relaxed">Botanical fibers from sustainably harvested beech trees, known for exceptional breathability.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-br from-[#1a1a1a] to-[#0a0a0a] border border-white/5 p-8 relative overflow-hidden">
                        <div class="absolute top-0 right-0 w-64 h-64 bg-white/5 rounded-full blur-3xl"></div>
                        <div class="relative z-10">
                            <h3 class="text-2xl font-bold mb-8 tracking-tight">Quality Standards</h3>
                            <ul class="space-y-6">
                                <li class="flex items-start gap-4">
                                    <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                    <div>
                                        <span class="block font-bold mb-1">OEKO-TEX® Standard 100</span>
                                        <span class="text-sm text-gray-400">Certified free from harmful substances</span>
                                    </div>
                                </li>
                                <li class="flex items-start gap-4">
                                    <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                    <div>
                                        <span class="block font-bold mb-1">GOTS Certified Organic</span>
                                        <span class="text-sm text-gray-400">Global Organic Textile Standard</span>
                                    </div>
                                </li>
                                <li class="flex items-start gap-4">
                                    <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                    <div>
                                        <span class="block font-bold mb-1">Bluesign® Approved</span>
                                        <span class="text-sm text-gray-400">Sustainable chemical management</span>
                                    </div>
                                </li>
                                <li class="flex items-start gap-4">
                                    <svg class="w-6 h-6 text-white flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"></path></svg>
                                    <div>
                                        <span class="block font-bold mb-1">Fair Trade Certified™</span>
                                        <span class="text-sm text-gray-400">Ethical production standards</span>
                                    </div>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="tab-content" id="content-styling">
                <div class="grid md:grid-cols-3 gap-6">
                    <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                        <img src="https://images.unsplash.com/photo-1483985988355-763728e1935b?w=600&q=80" class="w-full h-full object-cover" alt="Styling 1">
                        <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                            <div class="absolute bottom-0 left-0 right-0 p-8">
                                <h4 class="font-bold text-xl tracking-tight mb-2">Monochrome Layers</h4>
                                <p class="text-sm text-gray-400">3 ways to style black & white</p>
                            </div>
                        </div>
                    </div>
                    <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                        <img src="https://images.unsplash.com/photo-1469334031218-e382a71b716b?w=600&q=80" class="w-full h-full object-cover" alt="Styling 2">
                        <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                            <div class="absolute bottom-0 left-0 right-0 p-8">
                                <h4 class="font-bold text-xl tracking-tight mb-2">Essential Basics</h4>
                                <p class="text-sm text-gray-400">Building a capsule wardrobe</p>
                            </div>
                        </div>
                    </div>
                    <div class="img-zoom aspect-[3/4] bg-[#111] relative group cursor-pointer">
                        <img src="https://images.unsplash.com/photo-1445205170230-053b83016050?w=600&q=80" class="w-full h-full object-cover" alt="Styling 3">
                        <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500">
                            <div class="absolute bottom-0 left-0 right-0 p-8">
                                <h4 class="font-bold text-xl tracking-tight mb-2">Street Style</h4>
                                <p class="text-sm text-gray-400">Urban minimalism guide</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div class="section-divider max-w-7xl mx-auto"></div>

    <!-- Shop Section -->
    <section id="shop" class="py-32 bg-[#0a0a0a]">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="flex flex-col md:flex-row md:items-end md:justify-between mb-20 gap-8">
                <div>
                    <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Collection</p>
                    <h2 class="text-4xl md:text-6xl font-bold tracking-tighter">OUR BESTSELLER</h2>
                </div>
                
                <!-- Category Filter -->
                <div class="flex gap-4 flex-wrap">
                    <button onclick="filterProducts('all')" class="filter-btn active px-6 py-3 bg-white text-black text-xs font-bold tracking-widest uppercase transition-all" data-filter="all">All</button>
                    <button onclick="filterProducts('hoodies')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="hoodies">Hoodies</button>
                    <button onclick="filterProducts('tshirts')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="tshirts">T-Shirts</button>
                    <button onclick="filterProducts('posters')" class="filter-btn px-6 py-3 border border-white/20 text-gray-400 text-xs font-bold tracking-widest uppercase hover:border-white hover:text-white transition-all" data-filter="posters">Silver Posters</button>
                </div>
            </div>
            
            <!-- Products Grid -->
            <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6" id="products-grid">
                <!-- Products injected by JS -->
            </div>
        </div>
    </section>

    <div class="section-divider max-w-7xl mx-auto"></div>

    <!-- Services Section -->
    <section class="py-32 bg-[#0a0a0a]">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="grid lg:grid-cols-2 gap-16 items-center">
                <div>
                    <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">What We Offer</p>
                    <h2 class="text-4xl md:text-5xl font-bold tracking-tighter mb-12">OUR SERVICES</h2>
                    
                    <div class="space-y-8">
                        <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                            <div class="flex items-center gap-4">
                                <span class="text-gray-500 text-sm">01</span>
                                <span class="font-bold tracking-wide">Global Shipping</span>
                            </div>
                            <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                        </div>
                        <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                            <div class="flex items-center gap-4">
                                <span class="text-gray-500 text-sm">02</span>
                                <span class="font-bold tracking-wide">AI Design Consultation</span>
                            </div>
                            <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                        </div>
                        <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                            <div class="flex items-center gap-4">
                                <span class="text-gray-500 text-sm">03</span>
                                <span class="font-bold tracking-wide">Custom Branding</span>
                            </div>
                            <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                        </div>
                        <div class="flex items-center justify-between py-6 border-b border-white/10 group cursor-pointer hover:border-white/30 transition-colors">
                            <div class="flex items-center gap-4">
                                <span class="text-gray-500 text-sm">04</span>
                                <span class="font-bold tracking-wide">24/7 Support</span>
                            </div>
                            <svg class="w-5 h-5 text-gray-600 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                        </div>
                    </div>
                </div>
                
                <div class="relative">
                    <div class="img-zoom aspect-[4/5] bg-[#111]">
                        <img src="https://images.unsplash.com/photo-1552374196-1ab2a1c593e8?w=800&q=80" class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700" alt="Services">
                    </div>
                    <div class="absolute -bottom-6 -left-6 bg-white text-black p-6 max-w-xs">
                        <p class="text-xs font-bold tracking-widest uppercase mb-2">Premium Service</p>
                        <p class="text-sm font-medium">White-glove treatment for every order, from studio to doorstep.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Newsletter -->
    <section class="py-32 bg-[#111] border-y border-white/5">
        <div class="max-w-4xl mx-auto px-6 lg:px-8 text-center">
            <p class="text-xs font-medium tracking-[0.3em] uppercase text-gray-500 mb-4">Stay Updated</p>
            <h2 class="text-3xl md:text-5xl font-bold tracking-tighter mb-8">JOIN THE NEWSLETTER</h2>
            <p class="text-gray-400 mb-10 max-w-lg mx-auto">Be the first to know about exclusive drops, AI-generated collections, and member-only events.</p>
            
            <form class="flex flex-col sm:flex-row gap-4 max-w-md mx-auto" onsubmit="event.preventDefault(); alert('Thank you for subscribing!');">
                <input type="email" placeholder="Enter your email" class="flex-1 px-6 py-4 bg-[#0a0a0a] border border-white/10 text-white placeholder-gray-600 focus:outline-none focus:border-white/30 transition-colors text-sm">
                <button type="submit" class="px-8 py-4 bg-white text-black font-bold text-xs tracking-widest uppercase hover:bg-gray-200 transition-colors">
                    Subscribe
                </button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-[#0a0a0a] pt-20 pb-10">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="grid md:grid-cols-4 gap-12 mb-20">
                <div class="md:col-span-2">
                    <h3 class="text-lg font-bold tracking-[0.2em] uppercase mb-6">
                        Generations<span class="font-light opacity-60">Studios</span>
                    </h3>
                    <p class="text-gray-500 text-sm leading-relaxed max-w-sm mb-8">
                        Crafting cutting-edge lifestyle apparel for the modern consumer. Sustainable, minimal, timeless.
                    </p>
                    <div class="flex gap-4">
                        <a href="#" class="w-10 h-10 border border-white/10 flex items-center justify-center hover:border-white hover:bg-white hover:text-black transition-all">
                            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/></svg>
                        </a>
                        <a href="#" class="w-10 h-10 border border-white/10 flex items-center justify-center hover:border-white hover:bg-white hover:text-black transition-all">
                            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
                        </a>
                    </div>
                </div>
                <div>
                    <h4 class="font-bold text-xs tracking-widest uppercase mb-6 text-gray-400">Shop</h4>
                    <ul class="space-y-4 text-sm text-gray-500">
                        <li><a href="#" class="hover:text-white transition-colors">New Arrivals</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">Best Sellers</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">Hoodies</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">T-Shirts</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">Posters</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="font-bold text-xs tracking-widest uppercase mb-6 text-gray-400">Support</h4>
                    <ul class="space-y-4 text-sm text-gray-500">
                        <li><a href="#" class="hover:text-white transition-colors">Contact</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">Shipping</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">Returns</a></li>
                        <li><a href="#" class="hover:text-white transition-colors">Size Guide</a></li>
                    </ul>
                </div>
            </div>
            
            <div class="border-t border-white/10 pt-8 flex flex-col md:flex-row justify-between items-center gap-4">
                <p class="text-xs text-gray-600">© 2026 Generations Studios. All rights reserved.</p>
                <div class="flex gap-8 text-xs text-gray-600">
                    <a href="#" class="hover:text-white transition-colors">Terms</a>
                    <a href="#" class="hover:text-white transition-colors">Privacy</a>
                    <a href="#" class="hover:text-white transition-colors">Cookies</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- Cart Sidebar -->
    <div id="cart-sidebar" class="fixed inset-y-0 right-0 w-full md:w-[480px] bg-[#0a0a0a] border-l border-white/10 transform translate-x-full transition-transform duration-500 z-50 flex flex-col">
        <div class="p-8 border-b border-white/10 flex justify-between items-center">
            <h2 class="text-sm font-bold tracking-widest uppercase">Shopping Cart</h2>
            <button onclick="toggleCart()" class="p-2 hover:bg-white/5 rounded-full transition-colors">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
            </button>
        </div>
        
        <div class="flex-1 overflow-y-auto p-8" id="cart-items">
            <div class="text-center text-gray-600 mt-20">
                <div class="text-4xl mb-4 opacity-20">🛒</div>
                <p class="text-sm tracking-widest uppercase mb-4">Your cart is empty</p>
                <button onclick="toggleCart(); scrollToSection('shop')" class="text-xs font-bold tracking-widest uppercase text-white hover:text-gray-300 transition-colors border-b border-white/30 pb-1">
                    Start Shopping
                </button>
            </div>
        </div>
        
        <div class="border-t border-white/10 p-8 bg-[#111]" id="cart-footer" style="display: none;">
            <div class="flex justify-between mb-4 text-sm">
                <span class="text-gray-500 uppercase tracking-wider text-xs">Subtotal</span>
                <span class="font-bold" id="cart-subtotal">¥0.00</span>
            </div>
            <div class="flex justify-between mb-8 text-sm">
                <span class="text-gray-500 uppercase tracking-wider text-xs">Shipping</span>
                <span class="text-gray-400 text-xs">Calculated at checkout</span>
            </div>
            <div class="flex justify-between mb-8 text-lg font-bold">
                <span class="tracking-tight">Total</span>
                <span id="cart-total">¥0.00</span>
            </div>
            <button onclick="checkout()" class="w-full py-4 bg-white text-black font-bold text-xs tracking-widest uppercase hover:bg-gray-200 transition-all">
                Checkout
            </button>
        </div>
    </div>
    
    <!-- Overlay -->
    <div id="overlay" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-40 hidden opacity-0 transition-opacity duration-500" onclick="toggleCart()"></div>

    <!-- Search Modal -->
    <div id="search-modal" class="fixed inset-0 bg-[#0a0a0a]/98 backdrop-blur-md z-50 hidden flex items-center justify-center p-6">
        <button onclick="toggleSearch()" class="absolute top-8 right-8 p-2 hover:bg-white/5 rounded-full transition-colors">
            <svg class="w-8 h-8 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
        </button>
        <div class="w-full max-w-3xl">
            <input type="text" placeholder="Search products..." class="w-full text-5xl md:text-7xl font-bold bg-transparent border-b-2 border-white/20 pb-6 focus:outline-none focus:border-white placeholder-gray-800 text-center">
            <p class="mt-8 text-center text-gray-500 text-xs tracking-widest uppercase">Press Enter to search</p>
        </div>
    </div>

    <script>
        // Product Data
        const products = [
            {
                id: 1,
                name: "Essential Cotton Boxy T-Shirt",
                price: 14.38,
                category: "tshirts",
                image: "https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=600&q=80",
                description: "Ultra-soft organic cotton with a relaxed boxy fit."
            },
            {
                id: 2,
                name: "Essential Half Sleeve Ribbed T-Shirt",
                price: 23.95,
                category: "tshirts",
                image: "https://images.unsplash.com/photo-1583743814966-8936f5b7be1a?w=600&q=80",
                description: "Textured ribbed fabric with extended sleeves."
            },
            {
                id: 3,
                name: "Essential Heavyweight Fleece Hoodie",
                price: 63.96,
                category: "hoodies",
                image: "https://images.unsplash.com/photo-1556821840-3a63f95609a7?w=600&q=80",
                description: "Premium heavyweight fleece for maximum comfort."
            },
            {
                id: 4,
                name: "Mineral Wash Boxy Cotton T-Shirt",
                price: 19.98,
                category: "tshirts",
                image: "https://images.unsplash.com/photo-1576566588028-4147f3842f27?w=600&q=80",
                description: "Unique mineral wash treatment for vintage appeal."
            },
            {
                id: 5,
                name: "Silver Foil Graphic Poster - 'Ethereal'",
                price: 45.00,
                category: "posters",
                image: "https://images.unsplash.com/photo-1513519245088-0e12902e5a38?w=600&q=80",
                description: "Limited edition silver foil art print. 24x36 inches.",
                isSilver: true
            },
            {
                id: 6,
                name: "Silver Foil Graphic Poster - 'Monolith'",
                price: 45.00,
                category: "posters",
                image: "https://images.unsplash.com/photo-1505909182942-e2f09aee3e89?w=600&q=80",
                description: "Geometric silver foil design on museum-quality paper.",
                isSilver: true
            },
            {
                id: 7,
                name: "Oversized Zip-Up Hoodie",
                price: 72.00,
                category: "hoodies",
                image: "https://images.unsplash.com/photo-1556905055-8f358a7a47b2?w=600&q=80",
                description: "Modern oversized silhouette with premium hardware."
            },
            {
                id: 8,
                name: "Vintage Wash Long Sleeve",
                price: 28.50,
                category: "tshirts",
                image: "https://images.unsplash.com/photo-1618354691373-d851c5c3a990?w=600&q=80",
                description: "Long sleeve tee with subtle vintage wash finish."
            }
        ];

        // State
        let cart = [];
        let currentFilter = 'all';

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            renderProducts();
            generateCalendar();
            
            // Navbar scroll effect
            window.addEventListener('scroll', () => {
                const navbar = document.getElementById('navbar');
                if (window.scrollY > 50) {
                    navbar.classList.add('bg-[#0a0a0a]/95');
                } else {
                    navbar.classList.remove('bg-[#0a0a0a]/95');
                }
            });
        });

        // Render Products
        function renderProducts() {
            const grid = document.getElementById('products-grid');
            const filtered = currentFilter === 'all' 
                ? products 
                : products.filter(p => p.category === currentFilter);
            
            grid.innerHTML = filtered.map(product => `
                <div class="product-card group cursor-pointer animate-fade-in">
                    <div class="aspect-[4/5] overflow-hidden relative bg-[#111]">
                        <img src="${product.image}" alt="${product.name}" class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 group-hover:scale-105">
                        <button onclick="addToCart(${product.id})" class="absolute bottom-4 right-4 w-12 h-12 bg-white text-black rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transform translate-y-2 group-hover:translate-y-0 transition-all duration-300 hover:bg-gray-200">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                        </button>
                        ${product.isSilver ? '<span class="absolute top-4 left-4 px-3 py-1 bg-white text-black text-[10px] font-bold tracking-widest uppercase">Limited</span>' : ''}
                    </div>
                    <div class="p-6">
                        <h3 class="font-bold text-sm mb-2 tracking-tight group-hover:text-gray-300 transition-colors">${product.name}</h3>
                        <p class="text-gray-500 text-xs mb-3 line-clamp-1">${product.description}</p>
                        <p class="font-bold text-sm">¥${product.price.toFixed(2)}</p>
                    </div>
                </div>
            `).join('');
        }

        // Filter Products
        function filterProducts(category) {
            currentFilter = category;
            
            // Update buttons
            document.querySelectorAll('.filter-btn').forEach(btn => {
                if (btn.dataset.filter === category) {
                    btn.classList.add('bg-white', 'text-black', 'border-white');
                    btn.classList.remove('text-gray-400', 'border-white/20');
                } else {
                    btn.classList.remove('bg-white', 'text-black', 'border-white');
                    btn.classList.add('text-gray-400', 'border-white/20');
                }
            });
            
            renderProducts();
        }

        // Calendar Generation
        function generateCalendar() {
            const grid = document.getElementById('calendar-grid');
            const daysInMonth = 28;
            const startDay = 0;
            
            let html = '';
            for (let i = 0; i < startDay; i++) {
                html += '<div class="calendar-day text-gray-800"></div>';
            }
            
            const dropDays = [5, 12, 15, 19, 26];
            for (let i = 1; i <= daysInMonth; i++) {
                const hasDrop = dropDays.includes(i);
                const isSelected = i === 15;
                html += `<div class="calendar-day ${hasDrop ? 'has-drop' : ''} ${isSelected ? 'selected' : ''}" onclick="selectDate(${i})">${i}</div>`;
            }
            
            grid.innerHTML = html;
        }

        function selectDate(day) {
            document.querySelectorAll('.calendar-day').forEach(d => d.classList.remove('selected'));
            event.target.classList.add('selected');
            
            const titles = ['Urban Shadows', 'Midnight Cotton', 'Silver Linings', 'Monochrome Dreams', 'Essential Basics'];
            const images = [
                'https://images.unsplash.com/photo-1503341504253-dff4815485f1?w=1200&q=80',
                'https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=1200&q=80',
                'https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?w=1200&q=80',
                'https://images.unsplash.com/photo-1509631179647-0177331693ae?w=1200&q=80',
                'https://images.unsplash.com/photo-1490481651871-ab68de25d43d?w=1200&q=80'
            ];
            
            const index = (day % 5);
            document.getElementById('drop-title').textContent = titles[index] + ' Collection';
            document.getElementById('drop-image').src = images[index];
            document.getElementById('drop-date').textContent = `Feb ${day}, 2026`;
        }

        // Tab Switching
        function switchTab(tab) {
            document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
            document.getElementById(`content-${tab}`).classList.add('active');
            
            ['stories', 'fabric', 'styling'].forEach(t => {
                const btn = document.getElementById(`tab-${t}`);
                const indicator = btn.querySelector('span') || document.createElement('span');
                
                if (t === tab) {
                    btn.classList.remove('text-gray-500');
                    btn.classList.add('text-white');
                    if (!btn.querySelector('span')) {
                        indicator.className = 'absolute bottom-0 left-0 w-full h-0.5 bg-white';
                        btn.appendChild(indicator);
                    }
                } else {
                    btn.classList.add('text-gray-500');
                    btn.classList.remove('text-white');
                    const existingIndicator = btn.querySelector('span');
                    if (existingIndicator) existingIndicator.remove();
                }
            });
        }

        // Cart Functions
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const existing = cart.find(item => item.id === productId);
            
            if (existing) {
                existing.quantity++;
            } else {
                cart.push({ ...product, quantity: 1 });
            }
            
            updateCart();
            
            const badge = document.getElementById('cart-badge');
            badge.classList.add('cart-bounce');
            setTimeout(() => badge.classList.remove('cart-bounce'), 300);
            
            if (!document.getElementById('cart-sidebar').classList.contains('translate-x-0')) {
                toggleCart();
            }
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCart();
        }

        function updateQuantity(productId, delta) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity += delta;
                if (item.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    updateCart();
                }
            }
        }

        function updateCart() {
            const cartItems = document.getElementById('cart-items');
            const cartFooter = document.getElementById('cart-footer');
            const badge = document.getElementById('cart-badge');
            
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            
            if (totalItems > 0) {
                badge.textContent = totalItems;
                badge.classList.remove('hidden');
            } else {
                badge.classList.add('hidden');
            }
            
            if (cart.length === 0) {
                cartItems.innerHTML = `
                    <div class="text-center text-gray-600 mt-20">
                        <div class="text-4xl mb-4 opacity-20">🛒</div>
                        <p class="text-sm tracking-widest uppercase mb-4">Your cart is empty</p>
                        <button onclick="toggleCart(); scrollToSection('shop')" class="text-xs font-bold tracking-widest uppercase text-white hover:text-gray-300 transition-colors border-b border-white/30 pb-1">
                            Start Shopping
                        </button>
                    </div>
                `;
                cartFooter.style.display = 'none';
            } else {
                cartItems.innerHTML = cart.map(item => `
                    <div class="flex gap-6 mb-8 animate-fade-in">
                        <div class="w-24 h-24 bg-[#111] overflow-hidden flex-shrink-0">
                            <img src="${item.image}" alt="${item.name}" class="w-full h-full object-cover grayscale">
                        </div>
                        <div class="flex-1 flex flex-col justify-between">
                            <div>
                                <h4 class="font-bold text-sm mb-1 tracking-tight">${item.name}</h4>
                                <p class="text-gray-500 text-xs">¥${item.price.toFixed(2)}</p>
                            </div>
                            <div class="flex items-center justify-between">
                                <div class="flex items-center gap-4 border border-white/10 px-4 py-2">
                                    <button onclick="updateQuantity(${item.id}, -1)" class="text-gray-500 hover:text-white transition-colors">−</button>
                                    <span class="text-sm font-bold w-4 text-center">${item.quantity}</span>
                                    <button onclick="updateQuantity(${item.id}, 1)" class="text-gray-500 hover:text-white transition-colors">+</button>
                                </div>
                                <button onclick="removeFromCart(${item.id})" class="text-gray-600 hover:text-white transition-colors text-xs tracking-widest uppercase">
                                    Remove
                                </button>
                            </div>
                        </div>
                    </div>
                `).join('');
                
                cartFooter.style.display = 'block';
                document.getElementById('cart-subtotal').textContent = `¥${subtotal.toFixed(2)}`;
                document.getElementById('cart-total').textContent = `¥${subtotal.toFixed(2)}`;
            }
        }

        function toggleCart() {
            const sidebar = document.getElementById('cart-sidebar');
            const overlay = document.getElementById('overlay');
            
            if (sidebar.classList.contains('translate-x-full')) {
                sidebar.classList.remove('translate-x-full');
                sidebar.classList.add('translate-x-0');
                overlay.classList.remove('hidden');
                setTimeout(() => overlay.classList.remove('opacity-0'), 10);
                document.body.style.overflow = 'hidden';
            } else {
                sidebar.classList.add('translate-x-full');
                sidebar.classList.remove('translate-x-0');
                overlay.classList.add('opacity-0');
                setTimeout(() => overlay.classList.add('hidden'), 500);
                document.body.style.overflow = '';
            }
        }

        function checkout() {
            if (cart.length === 0) return;
            alert('Thank you for your purchase! Your order has been confirmed.');
            cart = [];
            updateCart();
            toggleCart();
        }

        // UI Functions
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        function toggleSearch() {
            const modal = document.getElementById('search-modal');
            if (modal.classList.contains('hidden')) {
                modal.classList.remove('hidden');
                setTimeout(() => modal.querySelector('input').focus(), 100);
            } else {
                modal.classList.add('hidden');
            }
        }

        function scrollToSection(id) {
            document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
        }

        function changeMonth(delta) {
            const grid = document.getElementById('calendar-grid');
            grid.style.opacity = '0';
            setTimeout(() => {
                generateCalendar();
                grid.style.opacity = '1';
            }, 200);
        }
    </script>
</body>
</html>


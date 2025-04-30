<section class="w-full min-h-[90dvh] px-4 md:px-20 py-8 md:py-10">
    <p class="font-extrabold text-xl md:text-2xl text-sky-600 text-center md:text-left">Kontak</p>
    <h1 class="font-bold text-4xl md:text-6xl text-slate-700 mt-3 text-center md:text-left">Mari Terhubung</h1>
    
    <div class="mt-10 grid grid-cols-1 md:grid-cols-2 gap-8">
        <div class="bg-white rounded-xl shadow-lg p-6">
            <h2 class="text-2xl font-bold text-slate-700">Hubungi Saya</h2>
            <form class="mt-6 space-y-4">
                <div>
                    <label class="block text-gray-700 mb-2" for="name">Nama</label>
                    <input type="text" id="name" class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-sky-600">
                </div>
                <div>
                    <label class="block text-gray-700 mb-2" for="email">Email</label>
                    <input type="email" id="email" class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-sky-600">
                </div>
                <div>
                    <label class="block text-gray-700 mb-2" for="message">Pesan</label>
                    <textarea id="message" rows="4" class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-sky-600"></textarea>
                </div>
                <button type="submit" class="w-full px-6 py-3 bg-sky-600 text-white rounded-lg hover:bg-sky-700 transition-colors">Kirim Pesan</button>
            </form>
        </div>
        
        <div class="bg-white rounded-xl shadow-lg p-6">
            <h2 class="text-2xl font-bold text-slate-700">Informasi Kontak</h2>
            <div class="mt-6 space-y-4">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 bg-sky-100 rounded-full flex items-center justify-center">
                        <svg class="w-5 h-5 text-sky-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                        </svg>
                    </div>
                    <div>
                        <p class="text-gray-600">Email</p>
                        <p class="text-slate-700 font-medium">email@example.com</p>
                    </div>
                </div>
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 bg-sky-100 rounded-full flex items-center justify-center">
                        <svg class="w-5 h-5 text-sky-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
                        </svg>
                    </div>
                    <div>
                        <p class="text-gray-600">Lokasi</p>
                        <p class="text-slate-700 font-medium">Yogyakarta, Indonesia</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
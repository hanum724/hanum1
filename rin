<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GlowGuide Pro - Konsultasi & Rekomendasi Skincare</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Poppins', sans-serif; }
    </style>
</head>
<body class="bg-rose-50 text-gray-800">

    <!-- Header / Navbar -->
    <header class="bg-white shadow-sm py-4 px-6 flex justify-between items-center sticky top-0 z-50">
        <h1 class="text-2xl font-bold text-rose-500">✨ GlowGuide Pro</h1>
        <nav class="space-x-4 text-sm font-medium">
            <a href="#consultation" class="hover:text-rose-500">Konsultasi Dokter</a>
            <a href="#budget-finder" class="hover:text-rose-500">Cari Sesuai Budget</a>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="text-center py-10 px-4 bg-gradient-to-b from-rose-100 to-rose-50">
        <h2 class="text-3xl font-bold text-gray-900 mb-2">Konsultasi Skincare & Rekomendasi Pas Budget</h2>
        <p class="text-gray-600 max-w-md mx-auto text-sm">Dapatkan rekomendasi rutinitas wajah langsung dari ahli dengan harga yang disesuaikan dengan dompetmu.</p>
    </section>

    <div class="max-w-4xl mx-auto p-4 grid md:grid-cols-2 gap-6">

        <!-- FITUR 1: Formulir Konsultasi Dokter -->
        <section id="consultation" class="bg-white p-6 rounded-2xl shadow-md border border-rose-100">
            <h3 class="text-lg font-bold text-rose-600 mb-1 flex items-center gap-2">
                🩺 Konsultasi Virtual Dokter
            </h3>
            <p class="text-xs text-gray-500 mb-4">Isi keluhan kulitmu untuk dijadwalkan dengan Dokter Estetika.</p>

            <form id="consultForm" onsubmit="handleConsultation(event)" class="space-y-3">
                <div>
                    <label class="block text-xs font-semibold mb-1">Nama Lengkap</label>
                    <input type="text" id="patientName" required placeholder="Contoh: Anisa" class="w-full p-2.5 text-sm border rounded-xl focus:ring-2 focus:ring-rose-400 outline-none">
                </div>
                <div>
                    <label class="block text-xs font-semibold mb-1">Keluhan Utama Kulit</label>
                    <select id="skinIssue" class="w-full p-2.5 text-sm border rounded-xl focus:ring-2 focus:ring-rose-400 outline-none">
                        <option value="Jerawat & Blemish">Jerawat & Bruntusan</option>
                        <option value="Kusam & Bekas Jerawat">Kusam & Bekas Jerawat</option>
                        <option value="Kulit Kering & Kaku">Kulit Kering & Sensitif</option>
                        <option value="Penuaan Dini">Garis Halus / Penuaan Dini</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold mb-1">Pesan / Catatan Tambahan</label>
                    <textarea id="patientNotes" rows="2" placeholder="Sebutkan produk yang sedang dipakai saat ini..." class="w-full p-2.5 text-sm border rounded-xl focus:ring-2 focus:ring-rose-400 outline-none"></textarea>
                </div>
                <button type="submit" class="w-full bg-rose-500 text-white py-2.5 rounded-xl font-medium text-sm hover:bg-rose-600 transition">
                    Kirim & Hubungi Dokter (WhatsApp)
                </button>
            </form>
        </section>

        <!-- FITUR 2: Smart Budget Skincare Recommendation -->
        <section id="budget-finder" class="bg-white p-6 rounded-2xl shadow-md border border-rose-100">
            <h3 class="text-lg font-bold text-rose-600 mb-1 flex items-center gap-2">
                💰 Rekomendasi Sesuai Budget
            </h3>
            <p class="text-xs text-gray-500 mb-4">Tentukan batas maksimal anggaran belanja skincare harianmu.</p>

            <div class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold mb-1">Pilih Tipe Kulit</label>
                    <select id="budgetSkinType" class="w-full p-2.5 text-sm border rounded-xl focus:ring-2 focus:ring-rose-400 outline-none">
                        <option value="berminyak">Berminyak / Berjerawat</option>
                        <option value="kering">Kering / Dehidrasi</option>
                    </select>
                </div>

                <div>
                    <label class="block text-xs font-semibold mb-1">Batas Maksimal Budget (Rp)</label>
                    <input type="number" id="maxBudget" placeholder="Contoh: 150000" class="w-full p-2.5 text-sm border rounded-xl focus:ring-2 focus:ring-rose-400 outline-none">
                </div>

                <button onclick="findSkincareByBudget()" class="w-full bg-emerald-600 text-white py-2.5 rounded-xl font-medium text-sm hover:bg-emerald-700 transition">
                    Cari Paket Skincare
                </button>

                <!-- Result Area -->
                <div id="budgetResult" class="hidden mt-4 p-4 bg-emerald-50 border border-emerald-200 rounded-xl">
                    <h4 class="font-bold text-emerald-800 text-sm mb-2">Rekomendasi Paket Produk:</h4>
                    <ul id="productList" class="text-xs text-gray-700 space-y-1 divide-y divide-emerald-100"></ul>
                    <div class="mt-3 pt-2 border-t border-emerald-200 flex justify-between font-bold text-xs text-emerald-900">
                        <span>Total Est. Harga:</span>
                        <span id="totalPrice">Rp 0</span>
                    </div>
                </div>
            </div>
        </section>

    </div>

    <!-- Footer -->
    <footer class="text-center py-6 text-xs text-gray-500 border-t bg-white mt-8">
        <p>&copy; 2026 GlowGuide Pro — Project Web TIK Kecantikan & Kesehatan</p>
    </footer>

    <!-- JavaScript Logic -->
    <script>
        // Database Produk Simulasi
        const productsDB = {
            berminyak: [
                { name: "Facial Wash Anti-Acne 100ml", price: 35000 },
                { name: "Niacinamide 5% Serum 20ml", price: 55000 },
                { name: "Lightweight Gel Moisturizer 30g", price: 45000 },
                { name: "Sunscreen Matte Finish SPF 30", price: 40000 }
            ],
            kering: [
                { name: "Gentle Hydrating Cleanser 100ml", price: 40000 },
                { name: "Hyaluronic Acid Serum 20ml", price: 60000 },
                { name: "Rich Moisture Cream 30g", price: 50000 },
                { name: "Hydrating Sunscreen SPF 50", price: 45000 }
            ]
        };

        // Handle Form Konsultasi
        function handleConsultation(e) {
            e.preventDefault();
            const name = document.getElementById('patientName').value;
            const issue = document.getElementById('skinIssue').value;
            const notes = document.getElementById('patientNotes').value;

            // Format Pesan WhatsApp
            const message = `Halo Dokter GlowGuide,%0ANama: ${name}%0AKeluhan: ${issue}%0ANote: ${notes}%0A%0AMohon bantuan konsul rekomendasi skincare.`;
            
            // Redirect ke WhatsApp (Nomor Contoh)
            window.open(`https://wa.me/6281234567890?text=${message}`, '_blank');
        }

        // Logic Filter Berdasarkan Budget
        function findSkincareByBudget() {
            const skinType = document.getElementById('budgetSkin

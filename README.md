<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <title>Anggi • Keuangan Jajan</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(145deg, #fef6e4 0%, #f9e4c8 100%);
            font-family: 'Segoe UI', 'Poppins', system-ui, -apple-system, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 16px;
        }

        .app-container {
            width: 100%;
            max-width: 420px;
            background: rgba(255, 248, 240, 0.85);
            backdrop-filter: blur(18px);
            -webkit-backdrop-filter: blur(18px);
            background: #fffbf4;
            border-radius: 40px;
            box-shadow: 0 25px 45px rgba(160, 100, 60, 0.25),
                        0 10px 20px rgba(0,0,0,0.1),
                        inset 0 1px 10px rgba(255,255,255,0.8);
            padding: 20px 20px 30px;
            display: flex;
            flex-direction: column;
            gap: 18px;
            border: 1px solid rgba(255, 215, 170, 0.7);
        }

        /* Header */
        .header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 8px 6px 0;
        }

        .app-title {
            font-size: 2.4rem;
            font-weight: 700;
            letter-spacing: -0.5px;
            background: linear-gradient(135deg, #b45f2a, #d97845);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 2px 2px 8px rgba(180, 95, 42, 0.2);
            line-height: 1.1;
        }

        .app-sub {
            font-size: 0.9rem;
            color: #b0724a;
            font-weight: 500;
            background: #fae3cd;
            padding: 5px 14px;
            border-radius: 30px;
            letter-spacing: 0.4px;
        }

        /* Card ringkasan saldo */
        .balance-card {
            background: #fbe9d7;
            border-radius: 28px;
            padding: 18px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: inset 0 1px 6px rgba(255,255,255,0.9), 0 12px 18px -10px rgba(170, 110, 20, 0.3);
            border: 1px solid #f7cfaa;
        }

        .balance-label {
            font-size: 0.9rem;
            font-weight: 600;
            color: #8b5a3a;
            text-transform: uppercase;
            letter-spacing: 0.6px;
        }

        .balance-amount {
            font-size: 2.2rem;
            font-weight: 800;
            color: #4b2e1a;
            display: flex;
            align-items: baseline;
            gap: 4px;
        }

        .balance-amount span {
            font-size: 1rem;
            font-weight: 600;
            color: #a4714a;
        }

        .reset-btn {
            background: #fff2e5;
            border: none;
            padding: 10px 16px;
            border-radius: 40px;
            font-weight: 700;
            color: #5f3b24;
            font-size: 0.8rem;
            display: flex;
            align-items: center;
            gap: 4px;
            cursor: pointer;
            transition: all 0.2s ease;
            box-shadow: 0 4px 8px rgba(150, 80, 20, 0.2);
            border: 1px solid #eecbad;
        }

        .reset-btn:hover {
            background: #ffe2cc;
            transform: scale(1.02);
            box-shadow: 0 6px 12px rgba(180, 90, 30, 0.25);
        }

        .reset-btn:active {
            transform: scale(0.96);
            background: #f8d3b0;
        }

        /* Daftar menu */
        .menu-grid {
            display: flex;
            flex-direction: column;
            gap: 14px;
            margin: 6px 0 4px;
        }

        .menu-item {
            background: #ffffff;
            border-radius: 26px;
            padding: 16px 18px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 8px 18px rgba(170, 120, 60, 0.12);
            border: 1px solid #ffede1;
            transition: all 0.2s ease;
            background: #fffbf7;
            cursor: pointer;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }

        .menu-item:active {
            background: #fff4e6;
            border-color: #e2b68b;
            transform: scale(0.98);
            box-shadow: 0 4px 10px rgba(200, 130, 50, 0.2);
        }

        .menu-info {
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .menu-name {
            font-size: 1.3rem;
            font-weight: 700;
            color: #482c1b;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .menu-price {
            font-size: 0.9rem;
            font-weight: 600;
            color: #b86f3c;
            background: #fae9da;
            padding: 3px 12px;
            border-radius: 20px;
            align-self: flex-start;
        }

        .quantity-badge {
            background: #d18d56;
            color: white;
            border-radius: 50px;
            padding: 6px 16px;
            font-weight: 700;
            font-size: 1.1rem;
            min-width: 50px;
            text-align: center;
            box-shadow: 0 4px 10px rgba(200, 120, 50, 0.4);
            transition: 0.1s;
        }

        /* total dan checkout */
        .summary-section {
            background: #fae9da;
            border-radius: 28px;
            padding: 18px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-top: 6px;
            border: 1px solid #edc7a3;
        }

        .total-text {
            font-weight: 700;
            font-size: 1.1rem;
            color: #633f28;
        }

        .total-price {
            font-weight: 800;
            font-size: 1.9rem;
            color: #3f2a19;
        }

        .checkout-btn {
            background: #c1723c;
            border: none;
            color: white;
            font-weight: 700;
            font-size: 1rem;
            padding: 12px 22px;
            border-radius: 40px;
            letter-spacing: 0.5px;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 10px 18px rgba(180, 90, 30, 0.5);
            border: 1px solid #f5ad7a;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .checkout-btn:hover {
            background: #b55d2c;
        }

        .checkout-btn:active {
            transform: scale(0.94);
            background: #9e4f26;
        }

        .footer-note {
            font-size: 0.7rem;
            text-align: center;
            color: #b28b6a;
            margin-top: 4px;
        }

        /* icon kecil */
        .emoji-icon {
            font-size: 1.4rem;
        }

        hr {
            border: 0.5px solid #f3d8bf;
            margin: 4px 0;
        }

        /* responsive kecil */
        @media (max-width: 380px) {
            .app-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <!-- Header ANGGI -->
        <div class="header">
            <div>
                <h1 class="app-title">Anggi</h1>
                <div class="app-sub">💰 jajan hemat</div>
            </div>
            <button class="reset-btn" id="resetButton">
                <span>↺</span> Reset
            </button>
        </div>

        <!-- Saldo / total pengeluaran hari ini -->
        <div class="balance-card">
            <div>
                <div class="balance-label">Total Pengeluaran</div>
                <div class="balance-amount">
                    Rp <span id="totalSpentDisplay">0</span>
                </div>
            </div>
            <div style="font-size:2rem; opacity:0.7;">🍿</div>
        </div>

        <!-- Daftar menu interaktif -->
        <div class="menu-grid" id="menuContainer">
            <!-- Item akan dirender melalui JavaScript agar dinamis dan terstruktur -->
        </div>

        <!-- Ringkasan dan checkout -->
        <div class="summary-section">
            <div>
                <div class="total-text">🧾 Total Pesanan</div>
                <div class="total-price" id="summaryTotal">Rp0</div>
            </div>
            <button class="checkout-btn" id="checkoutButton">
                <span>🛒</span> Beli
            </button>
        </div>
        <div class="footer-note">
            Klik menu untuk menambah · ANGGI jajan tracker
        </div>
    </div>

    <script>
        (function() {
            // --- DATA MENU APLIKASI ANGGI ---
            const menuItems = [
                {
                    id: 'esmilo',
                    name: 'Es Milo',
                    emoji: '🥤',
                    price: 7000,
                    colorTag: '#d48c4b'
                },
                {
                    id: 'cireng',
                    name: 'Cireng',
                    emoji: '🍘',
                    price: 5000,
                    colorTag: '#b8865a'
                },
                {
                    id: 'pancong',
                    name: 'Pancong Lumer',
                    emoji: '🥞',
                    price: 8000,
                    colorTag: '#c0814a'
                },
                {
                    id: 'chikuro',
                    name: 'Chikuro',
                    emoji: '🍢',
                    price: 6000,
                    colorTag: '#b57540'
                }
            ];

            // State pesanan: menyimpan jumlah per item
            let orderQuantities = {
                esmilo: 0,
                cireng: 0,
                pancong: 0,
                chikuro: 0
            };

            // DOM elements
            const menuContainer = document.getElementById('menuContainer');
            const totalSpentDisplay = document.getElementById('totalSpentDisplay');
            const summaryTotal = document.getElementById('summaryTotal');
            const resetButton = document.getElementById('resetButton');
            const checkoutButton = document.getElementById('checkoutButton');

            // Fungsi format rupiah
            const formatRupiah = (value) => {
                return value.toLocaleString('id-ID');
            };

            // Hitung total harga dari semua item
            const calculateTotal = () => {
                let total = 0;
                menuItems.forEach(item => {
                    const qty = orderQuantities[item.id] || 0;
                    total += qty * item.price;
                });
                return total;
            };

            // Update seluruh tampilan UI (kuantitas, total pengeluaran, total pesanan)
            const refreshUI = () => {
                // Update badge kuantitas tiap item
                menuItems.forEach(item => {
                    const qtyElement = document.getElementById(`qty-${item.id}`);
                    if (qtyElement) {
                        qtyElement.textContent = orderQuantities[item.id] || 0;
                    }
                });

                const total = calculateTotal();
                totalSpentDisplay.textContent = formatRupiah(total);
                summaryTotal.textContent = `Rp${formatRupiah(total)}`;
            };

            // Fungsi untuk menambah item (dipanggil saat klik menu)
            const addItem = (itemId) => {
                if (orderQuantities.hasOwnProperty(itemId)) {
                    orderQuantities[itemId] += 1;
                    refreshUI();
                    // Efek kecil getar / feedback (opsional visual)
                }
            };

            // Reset semua pesanan ke 0
            const resetAllOrders = () => {
                for (let key in orderQuantities) {
                    orderQuantities[key] = 0;
                }
                refreshUI();
                // Feedback singkat
                resetButton.style.transform = 'scale(0.9)';
                setTimeout(() => {
                    resetButton.style.transform = '';
                }, 120);
            };

            // Checkout / Beli : tampilkan pesan dan reset
            const handleCheckout = () => {
                const total = calculateTotal();
                if (total === 0) {
                    alert('🛍️ Kamu belum memilih jajan, nih. Klik menu dulu ya!');
                    return;
                }

                // Buat ringkasan pesanan
                let orderSummary = '';
                menuItems.forEach(item => {
                    const qty = orderQuantities[item.id];
                    if (qty > 0) {
                        orderSummary += `${item.emoji} ${item.name} x${qty} = Rp${formatRupiah(qty * item.price)}\n`;
                    }
                });

                const message = `🧾 *ANGGI - Struk Jajan* 🧾\n\n${orderSummary}\n━━━━━━━━━━━━━━\n💰 Total: Rp${formatRupiah(total)}\n\nTerima kasih sudah jajan! ✨`;
                alert(message);
                
                // Setelah checkout, reset pesanan (opsional: bisa tetap, tapi lebih baik reset)
                resetAllOrders();
            };

            // Membangun tampilan menu berdasarkan data
            const renderMenu = () => {
                if (!menuContainer) return;
                menuContainer.innerHTML = ''; // bersihkan

                menuItems.forEach(item => {
                    const itemDiv = document.createElement('div');
                    itemDiv.className = 'menu-item';
                    // Atribut data untuk identifikasi
                    itemDiv.setAttribute('data-id', item.id);
                    
                    // Konten dalam card
                    itemDiv.innerHTML = `
                        <div class="menu-info">
                            <div class="menu-name">
                                <span class="emoji-icon">${item.emoji}</span> ${item.name}
                            </div>
                            <div class="menu-price">Rp${formatRupiah(item.price)}</div>
                        </div>
                        <div class="quantity-badge" id="qty-${item.id}">0</div>
                    `;

                    // Event listener untuk klik (seluruh area card bisa diklik)
                    itemDiv.addEventListener('click', (e) => {
                        // Mencegah double trigger dari elemen dalam
                        addItem(item.id);
                        
                        // Animasi singkat pada badge
                        const badge = document.getElementById(`qty-${item.id}`);
                        if (badge) {
                            badge.style.transform = 'scale(1.2)';
                            setTimeout(() => {
                                badge.style.transform = 'scale(1)';
                            }, 100);
                        }
                    });

                    menuContainer.appendChild(itemDiv);
                });
            };

            // Inisialisasi event listener untuk tombol
            const bindEvents = () => {
                resetButton.addEventListener('click', resetAllOrders);
                checkoutButton.addEventListener('click', handleCheckout);
                
                // Opsional: bisa tambahkan keyboard shortcut (tidak perlu)
            };

            // Startup aplikasi
            const initApp = () => {
                renderMenu();
                // Pastikan state awal 0
                orderQuantities = {
                    esmilo: 0,
                    cireng: 0,
                    pancong: 0,
                    chikuro: 0
                };
                refreshUI();
                bindEvents();
            };

            // Jalankan setelah DOM siap
            window.addEventListener('DOMContentLoaded', initApp);
        })();
    </script>
</body>
</html>

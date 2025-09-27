<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Livros do Autor - [Seu Nome]</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            line-height: 1.6;
            color: #333;
            background: #f8f5f0;
        }

        .header {
            background: #2c1810;
            color: white;
            padding: 1rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #d4af37;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: #d4af37;
        }

        .cart-icon {
            position: relative;
            cursor: pointer;
        }

        .cart-count {
            background: #d4af37;
            color: #2c1810;
            border-radius: 50%;
            padding: 2px 6px;
            font-size: 0.8rem;
            position: absolute;
            top: -8px;
            right: -8px;
        }

        /* Modal do Carrinho */
        .cart-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }

        .cart-content {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            max-width: 500px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .cart-items {
            margin: 1rem 0;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
            border-bottom: 1px solid #ddd;
        }

        .cart-total {
            font-size: 1.3rem;
            font-weight: bold;
            text-align: center;
            margin: 1rem 0;
            color: #d4af37;
        }

        .btn {
            display: inline-block;
            padding: 12px 30px;
            background: #d4af37;
            color: #2c1810;
            text-decoration: none;
            border: none;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.3s;
            margin: 5px;
        }

        .btn:hover {
            background: #b8941f;
        }

        .btn-secondary {
            background: #2c1810;
            color: white;
        }

        .btn-secondary:hover {
            background: #1a0f09;
        }

        .whatsapp-btn {
            background: #25D366;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            font-size: 1.1rem;
        }

        .whatsapp-btn:hover {
            background: #128C7E;
        }

        .close-cart {
            float: right;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .hero {
            background: linear-gradient(rgba(44, 24, 16, 0.8), rgba(44, 24, 16, 0.8)),
                        url('https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d');
            background-size: cover;
            background-position: center;
            height: 70vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            margin-top: 60px;
        }

        .hero-content h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 4rem 2rem;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
            font-size: 2.5rem;
            color: #2c1810;
        }

        .books-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-bottom: 4rem;
        }

        .book-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }

        .book-card:hover {
            transform: translateY(-5px);
        }

        .book-image {
            width: 100%;
            height: 300px;
            background: #ddd;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: #666;
        }

        .book-info {
            padding: 1.5rem;
        }

        .book-title {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            color: #2c1810;
        }

        .book-price {
            font-size: 1.5rem;
            color: #d4af37;
            font-weight: bold;
            margin: 1rem 0;
        }

        .add-to-cart {
            width: 100%;
            padding: 10px;
            background: #2c1810;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .add-to-cart:hover {
            background: #d4af37;
            color: #2c1810;
        }

        .about {
            background: #2c1810;
            color: white;
            padding: 4rem 2rem;
        }

        .about-content {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
        }

        .footer {
            background: #2c1810;
            color: white;
            text-align: center;
            padding: 2rem;
        }

        .phone-number {
            font-size: 1.3rem;
            font-weight: bold;
            background: #25D366;
            color: white;
            padding: 15px;
            border-radius: 10px;
            margin: 1rem 0;
            display: inline-block;
        }

        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            .hero-content h1 {
                font-size: 2rem;
            }
            .hero {
                height: 50vh;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <nav class="nav-container">
            <div class="logo">LivrariaAutor</div>
            <div class="nav-links">
                <a href="#inicio">Início</a>
                <a href="#livros">Livros</a>
                <a href="#sobre">Sobre</a>
                <a href="#contato">Contato</a>
            </div>
            <div class="cart-icon" id="openCart">
                🛒 <span class="cart-count">0</span>
            </div>
        </nav>
    </header>

    <!-- Modal do Carrinho -->
    <div class="cart-modal" id="cartModal">
        <div class="cart-content">
            <span class="close-cart" id="closeCart">&times;</span>
            <h2>Seu Carrinho de Compras</h2>
            <div class="cart-items" id="cartItems">
                <!-- Itens do carrinho aparecerão aqui -->
            </div>
            <div class="cart-total" id="cartTotal">Total: R$ 0,00</div>
            
            <!-- Informações de Contato -->
            <div style="text-align: center; margin: 2rem 0;">
                <h3>📞 Para finalizar sua compra:</h3>
                <div class="phone-number">+244 935 491 375</div>
                <p>Entre em contato via WhatsApp para combinar pagamento e entrega</p>
            </div>

            <button class="btn whatsapp-btn" id="whatsappBtn">
                📱 Abrir WhatsApp
            </button>
            <button class="btn btn-secondary" id="clearCart">Esvaziar Carrinho</button>
            <button class="btn btn-secondary" id="continueShopping">Continuar Comprando</button>
        </div>
    </div>

    <!-- Hero Section -->
    <section id="inicio" class="hero">
        <div class="hero-content">
            <h1>Descubra Mundos Extraordinários</h1>
            <p>Livros escritos com paixão por [Seu Nome]</p>
            <a href="#livros" class="btn">Explorar Livros</a>
        </div>
    </section>

    <!-- Livros Section -->
    <section id="livros" class="container">
        <h2 class="section-title">Meus Livros</h2>
        <div class="books-grid">
            <!-- Livro 1 -->
            <div class="book-card">
                <div class="book-image">📖</div>
                <div class="book-info">
                    <h3 class="book-title">O Segredo do Amanhecer</h3>
                    <p>Uma aventura épica sobre coragem e descoberta.</p>
                    <div class="book-price">R$ 39,90</div>
                    <button class="add-to-cart" data-book="O Segredo do Amanhecer" data-price="39.90">
                        Adicionar ao Carrinho
                    </button>
                </div>
            </div>

            <!-- Livro 2 -->
            <div class="book-card">
                <div class="book-image">📖</div>
                <div class="book-info">
                    <h3 class="book-title">Sombras do Passado</h3>
                    <p>Um thriller psicológico que vai te prender até o final.</p>
                    <div class="book-price">R$ 34,90</div>
                    <button class="add-to-cart" data-book="Sombras do Passado" data-price="34.90">
                        Adicionar ao Carrinho
                    </button>
                </div>
            </div>

            <!-- Livro 3 -->
            <div class="book-card">
                <div class="book-image">📖</div>
                <div class="book-info">
                    <h3 class="book-title">O Último Portal</h3>
                    <p>Fantasia e magia em uma jornada inesquecível.</p>
                    <div class="book-price">R$ 42,90</div>
                    <button class="add-to-cart" data-book="O Último Portal" data-price="42.90">
                        Adicionar ao Carrinho
                    </button>
                </div>
            </div>
        </div>
    </section>

    <!-- Sobre Section -->
    <section id="sobre" class="about">
        <div class="container">
            <div class="about-content">
                <h2 class="section-title" style="color: white;">Sobre o Autor</h2>
                <p>[Sua história como autor - conte sobre sua paixão pela escrita, inspirações, etc.]</p>
                <p>Escrevo livros que transportam os leitores para mundos extraordinários, onde cada página é uma nova descoberta.</p>
            </div>
        </div>
    </section>

    <!-- Contato Section -->
    <section id="contato" class="container">
        <h2 class="section-title">Entre em Contato</h2>
        <form class="contact-form">
            <div class="form-group">
                <label for="nome">Nome:</label>
                <input type="text" id="nome" required>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" required>
            </div>
            <div class="form-group">
                <label for="mensagem">Mensagem:</label>
                <textarea id="mensagem" rows="5" required></textarea>
            </div>
            <button type="submit" class="btn">Enviar Mensagem</button>
        </form>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <p>&copy; 2024 [Seu Nome]. Todos os direitos reservados.</p>
        <p>Contacto: +244 935 491 375</p>
    </footer>

    <script>
        // Sistema de Carrinho
        let cart = [];
        const cartModal = document.getElementById('cartModal');
        const cartItems = document.getElementById('cartItems');
        const cartTotal = document.getElementById('cartTotal');
        const cartCount = document.querySelector('.cart-count');

        // Abrir carrinho
        document.getElementById('openCart').addEventListener('click', () => {
            updateCartDisplay();
            cartModal.style.display = 'flex';
        });

        // Fechar carrinho
        document.getElementById('closeCart').addEventListener('click', () => {
            cartModal.style.display = 'none';
        });

        document.getElementById('continueShopping').addEventListener('click', () => {
            cartModal.style.display = 'none';
        });

        // Esvaziar carrinho
        document.getElementById('clearCart').addEventListener('click', () => {
            cart = [];
            updateCartCount();
            updateCartDisplay();
        });

        // Botão WhatsApp
        document.getElementById('whatsappBtn').addEventListener('click', () => {
            const message = `Olá! Gostaria de comprar os seguintes livros:\n${cart.map(item => `- ${item.title} (R$ ${item.price})`).join('\n')}\nTotal: R$ ${calculateTotal()}`;
            const whatsappUrl = `https://wa.me/244935491375?text=${encodeURIComponent(message)}`;
            window.open(whatsappUrl, '_blank');
        });

        // Adicionar livros ao carrinho
        document.querySelectorAll('.add-to-cart').forEach(button => {
            button.addEventListener('click', function() {
                const bookTitle = this.getAttribute('data-book');
                const bookPrice = parseFloat(this.getAttribute('data-price'));
                
                // Verificar se o livro já está no carrinho
                const existingItem = cart.find(item => item.title === bookTitle);
                
                if (existingItem) {
                    existingItem.quantity += 1;
                } else {
                    cart.push({
                        title: bookTitle,
                        price: bookPrice,
                        quantity: 1
                    });
                }
                
                updateCartCount();
                
                // Feedback visual
                this.textContent = '✓ Adicionado!';
                this.style.background = '#27ae60';
                
                setTimeout(() => {
                    this.textContent = 'Adicionar ao Carrinho';
                    this.style.background = '';
                }, 2000);
            });
        });

        // Atualizar contador do carrinho
        function updateCartCount() {
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            cartCount.textContent = totalItems;
        }

        // Calcular total
        function calculateTotal() {
            return cart.reduce((sum, item) => sum + (item.price * item.quantity), 0).toFixed(2);
        }

        // Atualizar display do carrinho
        function updateCartDisplay() {
            cartItems.innerHTML = '';
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<p>Seu carrinho está vazio</p>';
                cartTotal.textContent = 'Total: R$ 0,00';
                return;
            }
            
            cart.forEach(item => {
                const itemElement = document.createElement('div');
                itemElement.className = 'cart-item';
                itemElement.innerHTML = `
                    <div>
                        <strong>${item.title}</strong><br>
                        <small>Quantidade: ${item.quantity}</small>
                    </div>
                    <div>R$ ${(item.price * item.quantity).toFixed(2)}</div>
                `;
                cartItems.appendChild(itemElement);
            });
            
            cartTotal.textContent = `Total: R$ ${calculateTotal()}`;
        }

        // Smooth Scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Form Submission
        document.querySelector('.contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Mensagem enviada com sucesso! Entrarei em contato em breve.');
            this.reset();
        });

        // Fechar modal clicando fora
        window.addEventListener('click', (e) => {
            if (e.target === cartModal) {
                cartModal.style.display = 'none';
            }
        });
    </script>
</body>
</html>

# Block-Wallet<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Global Wallet & Exchange</title>
    <link rel="stylesheet" href="style.css">
    <!-- FontAwesome para ícones -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>
    <div class="app-container">
        <!-- Barra Lateral / Menu -->
        <aside class="sidebar">
            <div class="logo">
                <i class="fa-solid fa-wallet"></i>
                <span>GlobalPay</span>
            </div>
            <ul class="menu">
                <li class="active"><a href="#"><i class="fa-solid fa-house"></i> Visão Geral</a></li>
                <li><a href="#converter"><i class="fa-solid fa-right-left"></i> Câmbio Global</a></li>
                <li><a href="#cards"><i class="fa-solid fa-credit-card"></i> Meus Cartões</a></li>
            </ul>
        </aside>

        <!-- Conteúdo Principal -->
        <main class="main-content">
            <header>
                <h1>Bem-vindo à sua Carteira Digital</h1>
                <p>Gerencie cartões e conversores globais em tempo real.</p>
            </header>

            <!-- Seção de Saldo e Ações Rápidas -->
            <section class="overview-grid">
                <div class="card balance-card">
                    <h3>Saldo Disponível Estimado</h3>
                    <div class="amount" id="totalBalance">$ 1,450.00 USD</div>
                    <span class="subtext">Atualizado automaticamente</span>
                </div>
            </section>

            <!-- Conversor Automático de Moedas -->
            <section id="converter" class="section-box">
                <h2><i class="fa-solid fa-earth-americas"></i> Conversor de Moedas Automático</h2>
                <div class="converter-grid">
                    <div class="input-group">
                        <label>Valor</label>
                        <input type="number" id="amountInput" value="100" placeholder="0.00">
                    </div>
                    <div class="input-group">
                        <label>De (Moeda)</label>
                        <select id="fromCurrency">
                            <option value="USD" selected>USD - Dólar Americano</option>
                            <option value="EUR">EUR - Euro</option>
                            <option value="AOA">AOA - Kwanza Angolano</option>
                            <option value="BRL">BRL - Real Brasileiro</option>
                            <option value="GBP">GBP - Libra Esterlina</option>
                            <option value="ZAR">ZAR - Rand Sul-Africano</option>
                        </select>
                    </div>
                    <div class="input-group">
                        <label>Para (Moeda de Destino)</label>
                        <select id="toCurrency">
                            <option value="AOA" selected>AOA - Kwanza Angolano</option>
                            <option value="USD">USD - Dólar Americano</option>
                            <option value="EUR">EUR - Euro</option>
                            <option value="BRL">BRL - Real Brasileiro</option>
                            <option value="GBP">GBP - Libra Esterlina</option>
                            <option value="ZAR">ZAR - Rand Sul-Africano</option>
                        </select>
                    </div>
                </div>
                <div class="result-box">
                    <span>Resultado Convertido:</span>
                    <h3 id="conversionResult">Carregando...</h3>
                </div>
            </section>

            <!-- Adicionar e Listar Cartões -->
            <section id="cards" class="section-grid">
                <div class="section-box">
                    <h2><i class="fa-solid id-card"></i> Adicionar Cartão (Simulação Express)</h2>
                    <form id="cardForm">
                        <div class="input-group">
                            <label>Nome no Cartão</label>
                            <input type="text" id="cardName" placeholder="Ex: Adilson A. Cristóvão" required>
                        </div>
                        <div class="input-group">
                            <label>Número do Cartão Visa/Express</label>
                            <input type="text" id="cardNumber" placeholder="4532 •••• •••• 8821" maxlength="19" required>
                        </div>
                        <div class="form-row">
                            <div class="input-group">
                                <label>Validade</label>
                                <input type="text" id="cardExp" placeholder="MM/AA" maxlength="5" required>
                            </div>
                            <div class="input-group">
                                <label>CVV (Segurança)</label>
                                <input type="password" id="cardCvv" placeholder="•••" maxlength="4" required>
                            </div>
                        </div>
                        <button type="submit" class="btn-primary">Vincular Cartão com Segurança</button>
                    </form>
                </div>

                <div class="section-box">
                    <h2>Seus Cartões Vinculados</h2>
                    <div id="cardsList" class="cards-list">
                        <!-- Cartões salvos aparecerão aqui dinamicamente -->
                        <div class="empty-card-notice">Nenhum cartão cadastrado ainda.</div>
                    </div>
                </div>
            </section>
        </main>
    </div>

    <script src="script.js"></script>
</body>
</html>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

body {
    background-color: #0f172a;
    color: #f8fafc;
    display: flex;
    min-height: 100vh;
}

.app-container {
    display: flex;
    width: 100%;
}

/* Sidebar */
.sidebar {
    width: 260px;
    background-color: #1e293b;
    padding: 2rem 1.5rem;
    display: flex;
    flex-direction: column;
    border-right: 1px solid #334155;
}

.logo {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 1.25rem;
    font-weight: bold;
    color: #38bdf8;
    margin-bottom: 2.5rem;
}

.menu {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.menu li a {
    display: flex;
    align-items: center;
    gap: 12px;
    color: #94a3b8;
    text-decoration: none;
    padding: 12px 15px;
    border-radius: 8px;
    transition: 0.3s;
}

.menu li.active a, .menu li a:hover {
    background-color: #38bdf8;
    color: #0f172a;
    font-weight: 600;
}

/* Main Content */
.main-content {
    flex: 1;
    padding: 2.5rem;
    overflow-y: auto;
}

header h1 {
    font-size: 1.8rem;
    margin-bottom: 5px;
}

header p {
    color: #94a3b8;
    margin-bottom: 2rem;
}

/* Cards de Visão Geral */
.overview-grid {
    margin-bottom: 2rem;
}

.balance-card {
    background: linear-gradient(135deg, #0284c7, #0369a1);
    padding: 1.5rem;
    border-radius: 12px;
    box-shadow: 0 4px 15px rgba(2, 132, 199, 0.3);
}

.balance-card h3 {
    font-size: 0.95rem;
    color: #e0f2fe;
    font-weight: 400;
}

.balance-card .amount {
    font-size: 2.2rem;
    font-weight: bold;
    margin: 10px 0 5px 0;
}

.subtext {
    font-size: 0.8rem;
    color: #bae6fd;
}

/* Seções e Caixas */
.section-box {
    background-color: #1e293b;
    padding: 1.5rem;
    border-radius: 12px;
    border: 1px solid #334155;
    margin-bottom: 2rem;
}

.section-box h2 {
    font-size: 1.2rem;
    margin-bottom: 1.2rem;
    display: flex;
    align-items: center;
    gap: 10px;
    color: #38bdf8;
}

.converter-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 15px;
    margin-bottom: 15px;
}

.input-group {
    display: flex;
    flex-direction: column;
    gap: 6px;
}

.input-group label {
    font-size: 0.85rem;
    color: #94a3b8;
}

.input-group input, .input-group select {
    padding: 10px 12px;
    background-color: #0f172a;
    border: 1px solid #475569;
    color: white;
    border-radius: 8px;
    font-size: 0.95rem;
}

.input-group input:focus, .input-group select:focus {
    outline: none;
    border-color: #38bdf8;
}

.result-box {
    background-color: #0f172a;
    padding: 12px 15px;
    border-radius: 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 1px dashed #475569;
}

.result-box span {
    color: #94a3b8;
    font-size: 0.9rem;
}

.result-box h3 {
    color: #34d399;
    font-size: 1.3rem;
}

/* Grid para cartões */
.section-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
}

.form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 15px;
}

.btn-primary {
    width: 100%;
    padding: 12px;
    background-color: #38bdf8;
    border: none;
    color: #0f172a;
    font-weight: bold;
    border-radius: 8px;
    cursor: pointer;
    transition: 0.3s;
}

.btn-primary:hover {
    background-color: #0ea5e9;
}

.cards-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
    max-height: 250px;
    overflow-y: auto;
}

.card-item {
    background: linear-gradient(135deg, #334155, #1e293b);
    padding: 15px;
    border-radius: 8px;
    border-left: 4px solid #38bdf8;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.card-info h4 {
    font-size: 0.95rem;
    margin-bottom: 3px;
}

.card-info p {
    font-size: 0.8rem;
    color: #94a3b8;
}

.empty-card-notice {
    color: #64748b;
    text-align: center;
    padding: 20px;
    font-style: italic;
}

/* Responsivo para Celulares */
@media(max-width: 768px) {
    body {
        flex-direction: column;
    }
    .sidebar {
        width: 100%;
        padding: 1rem;
    }
    .section-grid {
        grid-template-columns: 1fr;
    }
}
// Conversor de Moedas Automático usando API Pública Gratuita (ExchangeRate-API)
const amountInput = document.getElementById('amountInput');
const fromCurrency = document.getElementById('fromCurrency');
const toCurrency = document.getElementById('toCurrency');
const conversionResult = document.getElementById('conversionResult');

async function convertCurrency() {
    const amount = amountInput.value;
    const from = fromCurrency.value;
    const to = toCurrency.value;

    if (!amount || amount <= 0) {
        conversionResult.textContent = "Insira um valor válido";
        return;
    }

    try {
        // Buscando taxa de câmbio em tempo real atualizada
        const response = await fetch(`https://open.er-api.com/v6/latest/${from}`);
        const data = await response.json();

        if (data && data.rates && data.rates[to]) {
            const rate = data.rates[to];
            const converted = (amount * rate).toFixed(2);
            
            // Formatando o resultado visualmente
            conversionResult.textContent = `${converted} ${to}`;
        } else {
            conversionResult.textContent = "Erro na conversão";
        }
    } catch (error) {
        console.error("Erro ao buscar taxas de câmbio:", error);
        conversionResult.textContent = "Erro de conexão";
    }
}

// Ouvintes de eventos para conversão instantânea ao digitar ou mudar moedas
amountInput.addEventListener('input', convertCurrency);
fromCurrency.addEventListener('change', convertCurrency);
toCurrency.addEventListener('change', convertCurrency);

// Executar conversão inicial ao carregar a página
window.addEventListener('DOMContentLoaded', convertCurrency);


// Gestão de Cartões Visa / Express (Simulação Segura em Frontend)
const cardForm = document.getElementById('cardForm');
const cardsList = document.getElementById('cardsList');
let savedCards = [];

cardForm.addEventListener('submit', function(e) {
    e.preventDefault();

    const name = document.getElementById('cardName').value;
    const number = document.getElementById('cardNumber').value;
    const exp = document.getElementById('cardExp').value;

    // Mascarando o número do cartão para segurança visual (deixando apenas os últimos 4 dígitos)
    const lastDigits = number.slice(-4);
    const maskedNumber = `•••• •••• •••• ${lastDigits || '0000'}`;

    // Adicionando à lista de cartões do usuário
    const newCard = { name, maskedNumber, exp };
    savedCards.push(newCard);

    renderCards();
    cardForm.reset();
    alert('Cartão vinculado com sucesso à sua carteira Express!');
});

function renderCards() {
    if (savedCards.length === 0) {
        cardsList.innerHTML = `<div class="empty-card-notice">Nenhum cartão cadastrado ainda.</div>`;
        return;
    }

    cardsList.innerHTML = '';
    savedCards.forEach((card, index) => {
        cardsList.innerHTML += `
            <div class="card-item">
                <div class="card-info">
                    <h4>${card.name}</h4>
                    <p>${card.maskedNumber} | Exp: ${card.exp}</p>
                </div>
                <i class="fa-solid fa-check-circle" style="color: #34d399; font-size: 1.2rem;"></i>
            </div>
        `;
    });
}

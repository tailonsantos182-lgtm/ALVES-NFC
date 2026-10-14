<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ALVES NFC Sales - Simulador e Calculadora de Revenda</title>
    <style>
        :root {
            --bg-color: #0b0f19;
            --card-bg: #121826;
            --border-color: #1e293b;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --accent-blue: #3b82f6;
            --accent-green: #22c55e;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
        }

        header h1 {
            font-size: 1.8rem;
            margin-bottom: 5px;
            color: var(--text-main);
        }

        header p {
            color: var(--text-muted);
            font-size: 0.95rem;
        }

        .card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 20px;
        }

        h2 {
            font-size: 1.2rem;
            margin-top: 0;
            margin-bottom: 15px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 8px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.9rem;
        }

        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }

        th {
            color: var(--text-muted);
            font-weight: 600;
        }

        .price-normal {
            font-weight: bold;
        }

        .price-cupom {
            color: var(--accent-green);
            font-size: 0.85rem;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-size: 0.9rem;
            color: var(--text-muted);
        }

        select, input {
            width: 100%;
            padding: 10px;
            background-color: var(--bg-color);
            border: 1px solid var(--border-color);
            color: var(--text-main);
            border-radius: 6px;
            font-size: 1rem;
            box-sizing: border-box;
        }

        .results {
            background-color: var(--bg-color);
            border: 1px solid var(--border-color);
            padding: 15px;
            border-radius: 8px;
            margin-top: 15px;
        }

        .result-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 0.95rem;
        }

        .result-item.highlight {
            font-weight: bold;
            color: var(--accent-green);
            font-size: 1.1rem;
            border-top: 1px solid var(--border-color);
            padding-top: 8px;
            margin-top: 8px;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>3BM NFC Sales - Revenda</h1>
        <p>Tabela de Atacado e Calculadora de Lucro para Placas NFC de Avaliação Google</p>
    </header>

    <!-- Tabela de Atacado -->
    <div class="card">
        <h2>Tabela de Atacado (Preço por Unidade)</h2>
        <table>
            <thead>
                <tr>
                    <th>Faixa de Quantidade</th>
                    <th>Placa Parede (Azul/Preta)</th>
                    <th>Placa Balcão (Azul)</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>1 a 49 un</td>
                    <td><span class="price-normal">R$ 17,20</span><br><span class="price-cupom">R$ 16,70 c/ cupom</span></td>
                    <td><span class="price-normal">R$ 22,90</span><br><span class="price-cupom">R$ 21,90 c/ cupom</span></td>
                </tr>
                <tr>
                    <td>50 a 99 un</td>
                    <td><span class="price-normal">R$ 16,20</span><br><span class="price-cupom">R$ 15,70 c/ cupom</span></td>
                    <td><span class="price-normal">R$ 21,24</span><br><span class="price-cupom">R$ 20,24 c/ cupom</span></td>
                </tr>
                <tr>
                    <td>100 a 149 un</td>
                    <td><span class="price-normal">R$ 15,70</span><br><span class="price-cupom">R$ 15,20 c/ cupom</span></td>
                    <td><span class="price-normal">R$ 20,59</span><br><span class="price-cupom">R$ 19,59 c/ cupom</span></td>
                </tr>
                <tr>
                    <td>150 a 249 un</td>
                    <td><span class="price-normal">R$ 15,10</span><br><span class="price-cupom">R$ 14,60 c/ cupom</span></td>
                    <td><span class="price-normal">R$ 19,80</span><br><span class="price-cupom">R$ 18,80 c/ cupom</span></td>
                </tr>
                <tr>
                    <td>250+ un</td>
                    <td><span class="price-normal">R$ 14,90</span><br><span class="price-cupom">R$ 14,40 c/ cupom</span></td>
                    <td><span class="price-normal">R$ 19,54</span><br><span class="price-cupom">R$ 18,54 c/ cupom</span></td>
                </tr>
            </tbody>
        </table>
    </div>

    <!-- Calculadora de Lucro -->
    <div class="card">
        <h2>Calculadora de Lucro Personalizada</h2>
        
        <div class="form-group">
            <label for="tipoPlaca">Modelo da Placa:</label>
            <select id="tipoPlaca" onchange="calcularLucro()">
                <option value="parede">Placa NFC Parede (Azul ou Preta)</option>
                <option value="balcao">Placa NFC Balcão (Azul)</option>
            </select>
        </div>

        <div class="form-group">
            <label for="quantidade">Quantidade:</label>
            <input type="number" id="quantidade" value="10" min="1" oninput="calcularLucro()">
        </div>

        <div class="form-group">
            <label for="usarCupom">Aplicar Cupom de Desconto (R$ 0,50 a menos por unidade):</label>
            <select id="usarCupom" onchange="calcularLucro()">
                <option value="sim">Sim</option>
                <option value="nao">Não</option>
            </select>
        </div>

        <div class="form-group">
            <label for="precoVenda">Preço de Venda Sugerido por Unidade (R$):</label>
            <input type="number" id="precoVenda" value="45.00" step="0.50" oninput="calcularLucro()">
        </div>

        <div class="results">
            <div class="result-item">
                <span>Custo Unitário:</span>
                <span id="resCustoUnit">R$ 0,00</span>
            </div>
            <div class="result-item">
                <span>Custo Total de Compra:</span>
                <span id="resCustoTotal">R$ 0,00</span>
            </div>
            <div class="result-item">
                <span>Faturamento Previsto:</span>
                <span id="resFaturamento">R$ 0,00</span>
            </div>
            <div class="result-item highlight">
                <span>Lucro Total Estimado:</span>
                <span id="resLucroTotal">R$ 0,00</span>
            </div>
        </div>
    </div>
</div>

<script>
    function obterPrecoUnitario(tipo, qtd, comCupom) {
        let base = 0;
        let descontoCupom = comCupom ? 0.50 : 0;

        if (tipo === 'parede') {
            if (qtd < 50) base = 17.20;
            else if (qtd < 100) base = 16.20;
            else if (qtd < 150) base = 15.70;
            else if (qtd < 250) base = 15.10;
            else base = 14.90;
        } else { // balcao
            if (qtd < 50) base = 22.90;
            else if (qtd < 100) base = 21.24;
            else if (qtd < 150) base = 20.59;
            else if (qtd < 250) base = 19.80;
            else base = 19.54;
        }

        return Math.max(0, base - descontoCupom);
    }

    function calcularLucro() {
        const tipo = document.getElementById('tipoPlaca').value;
        const qtd = parseInt(document.getElementById('quantidade').value) || 0;
        const comCupom = document.getElementById('usarCupom').value === 'sim';
        const precoVenda = parseFloat(document.getElementById('precoVenda').value) || 0;

        const custoUnit = obterPrecoUnitario(tipo, qtd, comCupom);
        const custoTotal = custoUnit * qtd;
        const faturamento = precoVenda * qtd;
        const lucroTotal = faturamento - custoTotal;

        document.getElementById('resCustoUnit').innerText = `R$ ${custoUnit.toFixed(2).replace('.', ',')}`;
        document.getElementById('resCustoTotal').innerText = `R$ ${custoTotal.toFixed(2).replace('.', ',')}`;
        document.getElementById('resFaturamento').innerText = `R$ ${faturamento.toFixed(2).replace('.', ',')}`;
        document.getElementById('resLucroTotal').innerText = `R$ ${lucroTotal.toFixed(2).replace('.', ',')}`;
    }

    // Executar cálculo inicial ao carregar a página
    window.onload = calcularLucro;
</script>

</body>
</html>

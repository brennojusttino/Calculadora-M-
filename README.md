<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Calculadora de Metro Quadrado</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 500px;
      margin: 30px auto;
      padding: 20px;
      border: 2px solid #007bff;
      border-radius: 10px;
      background: #f4f4f4;
    }
    h2 {
      text-align: center;
      color: #007bff;
    }
    label {
      font-weight: bold;
      margin-top: 10px;
      display: block;
    }
    input, select {
      width: 100%;
      padding: 10px;
      margin: 5px 0 15px;
      font-size: 16px;
    }
    #resultado {
      background: #e2f7e2;
      padding: 12px;
      font-weight: bold;
      font-size: 18px;
      border-radius: 5px;
    }
  </style>
</head>
<body>

  <h2>Calculadora de Metro Quadrado</h2>

  <label for="valorMetro">Valor do metro quadrado (R$):</label>
  <input type="number" id="valorMetro" step="0.01" placeholder="Ex: 50.00">

  <label for="altura">Altura:</label>
  <input type="number" id="altura" step="0.01" placeholder="Ex: 200">

  <label for="largura">Largura:</label>
  <input type="number" id="largura" step="0.01" placeholder="Ex: 300">

  <label for="unidade">Unidade de medida:</label>
  <select id="unidade">
    <option value="mm">Milímetros (mm)</option>
    <option value="cm" selected>Centímetros (cm)</option>
    <option value="m">Metros (m)</option>
  </select>

  <div id="resultado">Preencha os campos para calcular.</div>

  <script>
    const campos = document.querySelectorAll('#valorMetro, #altura, #largura, #unidade');
    campos.forEach(campo => campo.addEventListener('input', calcular));

    function calcular() {
      const valorMetro = parseFloat(document.getElementById("valorMetro").value);
      const altura = parseFloat(document.getElementById("altura").value);
      const largura = parseFloat(document.getElementById("largura").value);
      const unidade = document.getElementById("unidade").value;
      const resultado = document.getElementById("resultado");

      if (isNaN(valorMetro) || isNaN(altura) || isNaN(largura)) {
        resultado.innerText = "Preencha todos os campos corretamente.";
        return;
      }

      let alturaM, larguraM;
      if (unidade === "mm") {
        alturaM = altura / 1000;
        larguraM = largura / 1000;
      } else if (unidade === "cm") {
        alturaM = altura / 100;
        larguraM = largura / 100;
      } else {
        alturaM = altura;
        larguraM = largura;
      }

      const area = alturaM * larguraM;
      const valorTotal = area * valorMetro;

      resultado.innerText = `Área: ${area.toFixed(2)} m²\nValor total: R$ ${valorTotal.toFixed(2)}`;
    }
  </script>

</body>
</html>

<script>
	// Variáveis de estado
	let peso = 0;      // Peso do usuário
	let altura = 0;    // Altura do usuário
	let imc = 0;       // Índice de Massa Corporal
	let classificacao = null; //Classificação do IMC
  
	// Função para calcular o IMC
	function calcularIMC() {
	  if (peso > 0 && altura > 0) {
		imc = (peso / Math.pow(altura, 2)).toFixed(2);
		regrasIMC(imc);
	  } else {
		imc = 0;
	  }
	}

	function regrasIMC(imc) {
		if (imc < 18.6){
			classificacao = 'Abaixo do Peso'
		}
		else if (imc >= 18.6 && imc < 25.0){
			classificacao = 'Peso Ideal (Parabéns)'
		}
		else if (imc >= 25.0 && imc < 30.0){
			classificacao = 'Levemente Acima do Peso'
		}
		else if (imc >= 30.0 && imc < 35.0){
			classificacao = 'Obesidade Grau I'
		}
		else if (imc >= 35.0 && imc < 40.0){
			classificacao = 'Obesidade Grau II (Severa)'
		}
		else if (imc >= 40){
			classificacao = 'Obesidade Grau III (Mórbida)'
		}
		else {
			classsificacao = 'IMC 0 ou Inválido'
		}
}

  </script>
  
  <main>
	<h1>Calculadora de IMC</h1>
	<label>
	  Peso (kg): <input type="number" bind:value={peso} on:input={calcularIMC} />
	</label>
	<label>
	  Altura (m): <input type="number" bind:value={altura} on:input={calcularIMC} />
	</label>
	{#if imc > 0}
	  <p>Seu IMC é {imc}</p>
	  <p>{classificacao}</p>
	{/if}
	
  </main>
  
  <style>
	main {
	  font-family: sans-serif;
	  text-align: center;
	  padding: 2rem;
	}
  
	h1 {
	  font-size: 1.5rem;
	  margin-bottom: 1rem;
	}
  
	label {
	  display: block;
	  margin-bottom: 0.5rem;
	}
  
	input {
	  padding: 0.25rem;
	}
  </style>
  
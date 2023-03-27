# CaixaEletronico
Caixa eletrônico funcional

var saldo = 100.5; //Float
		var senha_ja_informada = false;

		function identificacao(){
			var nome = prompt(`Qual o seu nome?`);
			alert(`Olá ${nome} é um prazer ter você aqui`);
			return nome;
		}

			var nomeUsuario = identificacao() // a variavel vai ser preenchida pelo que a função retornar 
			console.log(nomeUsuario)
			inicio()

			function acesso(){
				if(senha_ja_informada){
					return true;
				} else {
					var inserir_senha = prompt(`Digite sua senha`)

					if(inserir_senha == 666){
						return true;
					} else{
						alert('A senha está incorreta. Tente novamente.');
						acesso();
					}
				}
			}

			function inicio() {
				var escolha = parseInt(prompt('Selecione uma opção 1.) Saldo 2.) Depósito 3.) Saque 4.) Extrato 5.) Transferência 6.) Sair'));

				switch (escolha){
					case 1:
						ver_saldo();
						break;
					case 2:
						fazer_deposito();
						break;
					case 3:
						fazer_saque();
						break;
					case 4:
						extrato()
						break
					case 5:
						conta_transferencia()
						break
					case 6:
						sair();
						break;
					default:
						alert(`Escolha inválida. Tente novamente.`);
						inicio();
				}
			}		

			function ver_saldo() {
				if(acesso()){
					alert(`Seu saldo é: ${saldo}`);
					inicio();
				} else {
					ver_saldo();
				}
			}

			function fazer_deposito() {
				var deposito = parseFloat(prompt('Qual o valor para depósito?'));
				// Not a Number

				if (isNaN(deposito) || deposito === '') {
					alert('Por favor, informe um número:');
					fazer_deposito();
				} else if(deposito <= 0){
					alert('Operação não autorizada. O valor de depósito tem que ser maior que 0.')
				} else {
					saldo += deposito;
					// saldo = saldo + deposito;
					ver_saldo();
				}
			}

			function fazer_saque() { // ta pedindo a senha duas vezes
				var saque = parseFloat(prompt('Qual o valor para saque?'));

				if(acesso()){
					if(saque <= 0) {
					alert(`Operação não autorizada. O valor de saque tem que maior que 0.`)
					inicio()
				} else if (saque > saldo){
					alert(`Operação não autorizada. Seu saldo é menor que o valor de saque.`);
					ver_saldo()
					inicio()
				} else if (isNaN(saque) || saque === '') {
					alert('Por favor, informe um número:');
					fazer_saque();
				} else {
					saldo -= saque;
					senha_ja_informada = true;
					ver_saldo();
				}
					inicio();
				} else {
					ver_saldo()
				}
			}

			function erro() {
				alert('Por favor, informe um número entre 1 e 6');
				inicio();
			}

			function sair() { // ta repetindo 3 vezes e pede para informar o nome novamente 
				let confirma = confirm('Você deseja sair?');
				if (confirma) {
					alert(`${nomeUsuario}, foi um prazer ter você aqui!`)
					window.close();
				} else {
					inicio();
				}
			}

			sair()

			function extrato() {
				if(acesso()){
					alert(`Supermercado Da Praça: R$ 250,00\nMC Donalds: R$ 78,90\nShein: R$ 256,80\nAmazon: R$ 31,90`)
					inicio();
				} else {
					acesso()
				}
			}

			function conta_transferencia() { 
				
				var conta = parseInt(prompt(`Informe o número da conta que irá fazer a transferência.`))

				if(isNaN(conta) || conta === '' ){
					alert('Por favor, informe um número:');
					conta_transferencia();
				} else {
					valor_transferencia()
				}
			}

			function valor_transferencia() {
			var valor = parseFloat(prompt(`Informe o valor da transferência.`))

					if(valor <= 0) {
						alert(`Operação não autorizada. O valor de transferência tem que ser maior que 0.`)
						inicio()
					} else if (valor > saldo){
						alert(`Operação não autorizada. Seu saldo é menor que o valor de transferência.`);
						inicio()
					} else if ((isNaN(valor)) || valor === '') {
						alert('Por favor, informe um número:');
						valor_transferencia();
					} else {
						saldo -= valor;
						ver_saldo();
					}
				}
			
			identificacao();

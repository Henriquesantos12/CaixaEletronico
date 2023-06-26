# Caixa Eletrônico Funcional em JavaScript

## Descrição
Este é um projeto de um caixa eletrônico funcional desenvolvido em JavaScript. Ele permite realizar operações como autenticação com senha, saque e transferência de valores.

## Recursos

### Autenticação com Senha
- Solicita ao usuário que insira a senha para acessar o caixa eletrônico.
- Verifica se a senha inserida está correta.
- Permite um número máximo de tentativas de senha.

### Saque
- Permite ao usuário sacar um valor específico de sua conta.
- Verifica se o valor de saque é válido e se há saldo suficiente na conta.
- Atualiza o saldo da conta após o saque.

### Transferência
- Permite ao usuário transferir um valor específico para outra conta.
- Verifica se o valor de transferência é válido e se há saldo suficiente na conta.
- Atualiza o saldo da conta de origem e destino após a transferência.

## Lógica de Programação

### Autenticação com Senha
1. Solicite ao usuário que insira a senha.
2. Compare a senha inserida com a senha armazenada.
3. Se a senha for correta, dê acesso ao caixa eletrônico.
4. Caso contrário, informe que a senha está incorreta e dê a opção de tentar novamente.
5. Repita as etapas 1 a 4 até que a senha correta seja inserida ou o número máximo de tentativas seja atingido.

### Saque
1. Solicite ao usuário que insira o valor de saque.
2. Verifique se o valor de saque é válido (positivo e múltiplo das notas disponíveis).
3. Verifique se há saldo suficiente na conta para o saque.
4. Se todas as verificações forem bem-sucedidas, atualize o saldo da conta e entregue as notas correspondentes ao valor de saque.
5. Caso contrário, exiba uma mensagem informando o motivo pelo qual o saque não pode ser realizado.

### Transferência
1. Solicite ao usuário que insira o valor a ser transferido e a conta de destino.
2. Verifique se o valor da transferência é válido (positivo e menor ou igual ao saldo da conta de origem).
3. Verifique se a conta de destino é válida (existente no sistema).
4. Se todas as verificações forem bem-sucedidas, atualize o saldo da conta de origem e destino.
5. Caso contrário, exiba uma mensagem informando o motivo pelo qual a transferência não pode ser realizada.

## Exemplo de Uso

```javascript
// Função de autenticação com senha
function autenticarSenha(senha) {
  // Lógica de verificação da senha
}

// Função de saque
function sacar(valor) {
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
}

// Função de transferência
function transferir(valor, contaDestino) {
  // Lógica de verificação e atualização do saldo após a transferência
}

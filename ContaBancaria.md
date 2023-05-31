Public class ContaBancaria {
		
	Private static final int OP_TIPO_RETIDA = 1;
	Private static final int OP_TIPO_DEPOSITO = 0;

	Public static void main(String[] args) {
		int numeroConta = 0;
		float saldoConta = 0; 
		int operacao = 0;
		float valorTransacao = 0; 
		
		/**
		 * Se houver sucesso na operação um novo saldo será gerado, se não houver o saldo 
		 * permanece inalterado, para efeito de coerencia com a vida real das aplicações de
		 * ATM é bom manter o antigo o o novo saldo em variáveis distintas.
		 */
		float novoSaldo = 0;
		 
		
		/**
		 * Começe sempre lendo os valores da entrada, para isso crie a instancia do Scanner.
		 */
		Scanner input = new Scanner(System.in);
		
		/**
		 * Mostre sempre uma mensagem pedido alguma coisa ao usuário, antes de ler o valor 
		 * correspondente.
		 */
		System.out.print("Digite o Número da Conta? ");
		numeroConta = input.nextInt();
		
		System.out.print("Digite o Saldo da Conta? ");
		saldoConta = input.nextFloat();
		
		/**
		 * Atualize o novo saldo antes de iniciar a transação.
		 * No caso de não ter sucesso na transação o novo saldo é igual ao anterior.
		 */
		novoSaldo = saldoConta;
		
		System.out.print("Digite o tipo de operação [0 = DEPÓSITO / 1 = RETIRADA] ? ");
		operacao = input.nextInt();
		
		System.out.print("Digite o valor da Transação? ");
		valorTransacao = input.nextFloat();
		
		/**
		 * Processamento, agora que você tem as informações do usuário sobre
		 * a transação é hora de processar a transação.
		 */
		
		/**
		 * Verifique se a operação informada é valida
		 */
		if(operacao == OP_TIPO_DEPOSITO  || operacao == OP_TIPO_RETIDA ){
			
			//Evite if quando há varias opções para checar
			switch(operacao){
				case OP_TIPO_DEPOSITO:
					//Faça o deposito na conta
					novoSaldo = saldoConta + valorTransacao;
					break;
				case OP_TIPO_RETIDA:
					//Faca a retira da conta
					novoSaldo = saldoConta - valorTransacao;
					break;
			}
			
			/**
			 * Mostre para o usuário um saida após o processamento.
			 * Como um "extrato da conta" para conferencia
			 * 
			 */
			System.out.println("++++++++++++++++ Extrato Conta +++++++++++++++++++++");
			System.out.println(" - Número            \t\t\t    " + numeroConta);
			System.out.println(" - Saldo  Anterior   \t\t\t R$ " + saldoConta);
			System.out.println(" - Operação          \t\t\t    " + ((operacao == OP_TIPO_DEPOSITO) ? "DEPOSITO":"RETIRADA") );
			System.out.println(" - Valor             \t\t\t R$ " + valorTransacao);
			System.out.println(" - Saldo Atual       \t\t\t R$ " + novoSaldo);
			System.out.println("++++++++++++++++++++++++++++++++++++++++++++++++++++");
			
			/**
			 * Verifique se a condição em que o saldo é negativo.
			 */
			if(novoSaldo < 0){
				System.out.println("          ** Conta Estourada ***              ");
			}
		}
		else{
			System.out.println("Operação informada é Inválida!");
			System.out.println("Digite 0 para Deposito ou 1 para retirada");
			System.out.println("Por favor tente novamente!");
		}
		
		
		/**
		 * OBS: Uso do operador ternário do Java e  o \t é uma tabulação
		 * 
		 * 
		 * ((operacao == OP_TIPO_DEPOSITO) ? "DEPOSITO":"RETIRADA")
		 * 
		 * Equivalente a seguinte construção
		 * 
		 * if (operacao == OP_TIPO_DEPOSITO ){
		 *   return "DEPOSITO";
		 * }
		 * else {
		 *   return "RETIRADA";
		 * }
		 * 
		 * é uma curta de fazermos um IF.
		 */
	}
}

Public class ContaBancaria {
		
	Private static final int OP_TIPO_RETIDA = 1;
	Private static final int OP_TIPO_DEPOSITO = 0;

	Public static void main(String[] args) {
		int numeroConta = 0;
		float saldoConta = 0; 
		int operacao = 0;
		float valorTransacao = 0; 
		float novoSaldo = 0;
		Scanner input = new Scanner(System.in);
		
		System.out.print("Digite o Número da Conta? ");
		numeroConta = input.nextInt();
		
		System.out.print("Digite o Saldo da Conta? ");
		saldoConta = input.nextFloat();
		novoSaldo = saldoConta;
		
		System.out.print("Digite o tipo de operação [0 = DEPÓSITO / 1 = RETIRADA] ? ");
		operacao = input.nextInt();
		
		System.out.print("Digite o valor da Transação? ");
		valorTransacao = input.nextFloat();
		
		if(operacao == OP_TIPO_DEPOSITO  || operacao == OP_TIPO_RETIDA ){
			
			switch(operacao){
				case OP_TIPO_DEPOSITO:
					novoSaldo = saldoConta + valorTransacao;
					break;
				case OP_TIPO_RETIDA:
					novoSaldo = saldoConta - valorTransacao;
					break;
			}
			
		System.out.println("++++++++++++++++ Extrato Conta +++++++++++++++++++++");
		System.out.println(" - Número            \t\t\t    " + numeroConta);
		System.out.println(" - Saldo  Anterior   \t\t\t R$ " + saldoConta);
		System.out.println(" - Operação          \t\t\t    " + ((operacao == OP_TIPO_DEPOSITO) ? "DEPOSITO":"RETIRADA") );
		System.out.println(" - Valor             \t\t\t R$ " + valorTransacao);
		System.out.println(" - Saldo Atual       \t\t\t R$ " + novoSaldo);
		System.out.println("++++++++++++++++++++++++++++++++++++++++++++++++++++");
			
		if(novoSaldo < 0){
			System.out.println("          ** Conta Estourada ***              ");
			}
		}
		else{
			System.out.println("Operação informada é Inválida!");
			System.out.println("Digite 0 para Deposito ou 1 para retirada");
			System.out.println("Por favor tente novamente!");
		}
	}
}

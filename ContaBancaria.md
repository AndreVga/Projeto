Package Cooperado.Sicoob.Credivar;
import java.util.Scanner;
import java.time.localdate;
Public class ContaBancaria {
		
	Private static final int OP_Retirada = 1; /**Operação de Retirada*/
	Private static final int OP_Deposito = 0; /**Operação de Deposito*/

	Public static void main(String[] args) {
		string cooperado; /**Nome do Cooperado*/
            int numeroConta = 0; /**ID Único*/
		float saldoConta = 0; 
		int operacao = 0;
		float valorTransacao = 0; 
		float saldoAtual = 0;
        localdate data = localdate.now();

		Scanner input = new Scanner(System.in);
		
		System.out.print("Digite o Nome do Cooperado: ");
        cooperado = input.nextInt();

        System.out.print("Digite o Número da Conta: ");
		numeroConta = input.nextInt();
		
		/**System.out.print("Digite o Saldo da Conta? ");
		saldoConta = input.nextFloat();
		saldoAtual = saldoConta;
		/*/

		System.out.print("Digite o tipo de operação [0 = DEPÓSITO / 1 = RETIRADA] ? ");
		operacao = input.nextInt();
		
		System.out.print("Digite o valor da Transação? ");
		valorTransacao = input.nextFloat();
		
		if(operacao == OP_Deposito  || operacao == OP_Retirada ){ 
			
			switch(operacao){
				case OP_Deposito: 
					saldoAtual = saldoConta + valorTransacao;
					break;
				case OP_Retirada:
					saldoAtual = saldoConta - valorTransacao;
					break; 
			}

		System.out.println("++++++++++++++++ Extrato da Conta Corrente +++++++++++++++++++++");
		System.out.println("                 ---- SICOOB CREDIVAR ----                      ");
                System.out.println(" ");
                System.out.println(" - Nome do Cooperado   \t\t\t       " + cooperado);
                System.out.println(" - Número da Conta      \t\t\t      " + numeroConta);
		System.out.println(" - Saldo Anterior        \t\t\t  R$ " + saldoConta);
		System.out.println(+ data.toString());
                System.out.println(" - Operação Efetuada      \t\t\t    " + ((operacao == OP_Deposito) ? "DEPOSITO":"RETIRADA") );
		System.out.println(" - Valor da Transação     \t\t\t R$ " + valorTransacao);
		System.out.println(+ data.toString());
                System.out.println(" - Saldo Atual            \t\t\t R$ " + saldoAtual);
                System.out.println(+ data.toString());
                System.out.println(" ");
		System.out.println("+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++");
			
		if(saldoAtual < 0){
			System.out.println("          ****---Saldo Insuficiente---****              ");
			}
		}
		else{
			System.out.println("Operação informada é Inválida!");
			System.out.println("Digite 0 para Deposito ou 1 para retirada");
			System.out.println("Por favor tente novamente!");
		}
	}
}

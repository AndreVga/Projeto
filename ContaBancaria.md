Package Cooperado.Sicoob.Credivar;

import java.util.Scanner;
import java.time.LocalDate;
import java.time.LocalDateTime;

Public class ContaBancaria {	

	Private static final int OP_Retirada = 1; /**Operação de Retirada*/
	Private static final int OP_Deposito = 0; /**Operação de Deposito*/

	Public static void main(String[] args) {
		string cooperado; /**Nome do Cooperado.*/
            int ID = 0; /**ID Único para Identificação do Cooperado.*/
            int numeroConta = 0;
		float saldoConta = 0; 
		int operacao = 0;
		float valorTransacao = 0; 
		float saldoAtual = 0;
            LocalDate data = LocalDate.now();
            LocalDateTime time = LocalDateTime.now(); 

		Scanner input = new Scanner(System.in);
		
		System.out.println("Digite seu ID: ");
            ID = input.nextInt();

            System.out.println("Digite o Nome do Cooperado: ");
            cooperado = input.nextInt();

            System.out.println("Digite o Número da Conta: ");
		numeroConta = input.nextInt();
		
		System.out.println("Digite o Saldo da Conta: ");
		saldoConta = input.nextFloat();
		saldoAtual = saldoConta;
		
		System.out.println("Digite o tipo de operação [0 = DEPÓSITO / 1 = RETIRADA] ? ");
		operacao = input.nextInt();
		
		System.out.println("Digite o Valor da Transação: ");
		valorTransacao = input.nextFloat();
		
		if(operacao == OP_Deposito  || operacao == OP_Retirada){ 
			
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
            System.out.println("                                              " + time.toString());
            System.out.println(" ");
            System.out.println(" - ID:                                            \t\t\t       " + ID);
            System.out.println(" - Nome do Cooperado:                      \t\t\t       " + cooperado);
            System.out.println(" - Número da Conta:                       \t\t\t      " + numeroConta);
		System.out.println(" - Saldo Anterior:                      \t\t\t  R$ " + saldoConta);
		System.out.println(+ data.toString());
            System.out.println(" - Operação Efetuada:      \t\t\t    " + ((operacao == OP_Deposito) ? "DEPOSITO":"RETIRADA") );
		System.out.println(" - Valor da Transação:               \t\t\t R$ " + valorTransacao);
		System.out.println(+ data.toString());
            System.out.println(" - Saldo Atual:                               \t\t\t R$ " + saldoAtual);
            System.out.println(+ data.toString());
            System.out.println(" ");
		System.out.println("+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++");
		
            if(saldoAtual < 0){
			System.out.println("          ****---Saldo Insuficiente---****              ");
			}
		}
		else{
			System.out.println("Operação informada é Inválida!");
                        System.out.println("Por favor, tente novamente!");
			System.out.println("Digite 0 (Zero) para Deposito ou 1 para Retirada");
		}
	}
	        /**Rotina para ser programada no botão para Editar / Alterar o Cadastro do Cooperado.*/
	        Public void actionPerformed (ActionEvent e){ 
		
		If(id.getText().equals(" ")){ /**Comando que irá verificar se foi informado o ID para ser excluído.*/
		
		JOptionPane.showMessageDialog(null, "Favor Informar o ID!"); /**Mostrar mensagem.*/
		
		}else{
		
		estrutura est = new estrutura(Integer.parseInt(id.getText()), cooperado.getText(), numeroConta.getText(), saldoConta.getText(), operacao.getText(), valorTransacao.getText(), saldoAtual.getText());
		est.Editar();
		}
	}
	        /**Rotina para ser programada no botão Salvar o Cadastro do Cooperado.*/
	        Public void actionPerformed(ActionEvent e){ 
		
		If(id.getText().equals(" ")  ||  cooperado.getText().equals(" ")  ||  numeroConta.getText().equals(" ")  ||  saldoConta.getText().equals(" ")  || operacao.getText().equals(" ")  ||  valorTransacao.getText().equals(" ")  ||  saldoAtual.getText().equals(" ")){ 
	
		JOptionPane.showMessageDialog(null, "Favor Preencher as infomações do Cadastro!"); 
	
		}else{
	
		estrutura est = new estrutura(id.getText(), cooperado.getText(), numeroConta.getText(), saldoConta.getText(), operacao.getText(), valorTransacao.getText(), saldoAtual.getText());
		est.salvar();
	
		/** Comando para deixar os campos em branco "Limpo".*/
		id.setText(" ");
		cooperado.setText(" ");
		numeroConta.setText(" ");
		saldoConta.setText(" ");
		operacao.setText(" ");
		valorTransacao.setText(" "); 
		saldoAtual.setText(" ");
		}
	}
	        /**Rotina para ser programada no botão de Exclusão*/
	        Public void actionPerformed(ActionEvent e){ /**Rotina de conexão ao Banco de Dados para exclusão de cadastro.*/
		
		If(id.getText().equals(" ")){ /**Comando que irá verificar se foi informado o ID para ser excluído.*/
		
		JOptionPane.showMessageDialog(null, "Favor Informar o ID!"); 
		
		}else{
		try {
		
		Connection con = contaBancaria();
		string sql = "delete from cadastro where id=?"; /**Cadastro é o nome da minha "Tabela de Informações" dos cooperados.*/
		PreparedStatement stmt = con.prepareStatement(sql); 
		
		stmt.setString(1, id.getText());
		stmt.execute();
		stmt.close();
		con.close();
	
		JOptionPane.showMessageDialog(null, "Cadastro Excluído com Sucesso!"); /**Linha de comando que mostrará que o cadastro foi excluído com sucesso.*/

		/** Comando para deixar os campos em branco "Limpo".*/
		id.setText(" ");
		cooperado.setText(" ");
	        numeroConta.setText(" ");
		saldoConta.setText(" ");
		operacao.setText(" ");
		valorTransacao.setText(" "); 
		saldoAtual.setText(" ");
		}
			catch (SQLException el){
			el.printStackTrace();
			}
		}
	}
}

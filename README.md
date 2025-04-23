# DIO - Trilha Java Básico

## Controle de Fluxo - Desafio

O sistema deverá receber dois parâmetros via terminal que representarão dois números inteiros, com estes dois números você deverá obter a quantidade de interações (for) e realizar a impressão no console (System.out.print) dos números incrementados, exemplo:

* Se você passar os números 12 e 30, logo teremos uma interação (for) com 18 ocorrências para imprimir os números, exemplo: `"Imprimindo o número 1"`, `"Imprimindo o número 2"` e assim por diante.
* Se o primeiro parâmetro for MAIOR que o segundo parâmetro, você deverá lançar a exceção customizada chamada de `ParametrosInvalidosException` com a segunda mensagem: "O segundo parâmetro deve ser maior que o primeiro"   

1. Crie o projeto `DesafioControleFluxo`
2. Dentro do projeto, crie a classe `Contador.java` para realizar toda a codificação do nosso programa.
3. Dentro do projeto, crie a classe `ParametrosInvalidosException` que representará a exceção de negócio no sistema. 


## Resolução do Desafio:

```java
package controleFluxo;

import java.util.Scanner;
import java.util.InputMismatchException;

public class Contador {
	public static void main(String[] args) throws ParametrosInvalidosException {
		Scanner terminal = new Scanner(System.in);
		
		try {
			System.out.println("Digite o primeiro parâmetro");
			int parametroUm = terminal.nextInt();
			
			System.out.println("Digite o segundo parâmetro");
			int parametroDois = terminal.nextInt();
			
			contar(parametroUm, parametroDois);
			
		} catch (ParametrosInvalidosException e) {
			System.out.println(e.getMessage());
		} catch (InputMismatchException e) {
			System.out.println("Os parâmetros devem ser número inteiros");
		} finally {
			terminal.close();
		}
	}
	
	static void contar(int parametroUm, int parametroDois) throws ParametrosInvalidosException {
		if (parametroUm >= parametroDois) {
			throw new ParametrosInvalidosException("O segundo parâmetro deve ser maior que o primeiro!");
		}
		
		int contagem = parametroDois - parametroUm;
		for (int i = 1; i <= contagem; i ++) {
			System.out.println("Imprimindo o número " + i);
		}
	}
}

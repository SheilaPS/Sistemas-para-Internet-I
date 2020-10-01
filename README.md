# Sistemas-para-Internet-I
Tópicos Especiais em Sistemas para Internet I

package exerciseone; // nomes de pacotes são escritos em minúsculo em Java.

/**
 * proposal: 1. Implemente uma classe chamada Aluno para deﬁnir os objetos que
 * representarão os alunos de uma escola. Essa classe deve declarar três
 * atributos: o primeiro para o nome, o segundo para o RG e o terceiro para a
 * data de nascimento dos alunos. Realize o teste desta classe criando
 * instancias da classe Aluno..
 * 
 * @author Eduardo Rocha
 * 
 */
public class Student { // Classe é escrita em maiúscula.

	/**
	 *  [NOTA]: Observe que o Java utiliza como convenção a utilização da convenção(Sugestão) camelCase
	 * neste exemplo temos o atributo dateOfBirth utilizando a convenção, trata-se da primeira palavra ser escrita em 
	 * caixa baixa e as palvras subsequentes por caixa alta, isso facilita a leitura.
	 */
	
	// attributes
	String name;
	String rg;
	String dateOfBirth;

	// Constructor
	public Student(String name, String rg, String dateOfBirth) {
		super();
		this.name = name;
		this.rg = rg;
		this.dateOfBirth = dateOfBirth;
	}

	/*
	 * Aqui estamos sobrescrevendo o método toString de forma a representar de forma
	 * textual nosso objeto. pois seu objeto retorna o nome da classe mais uma
	 * representação hexadecimal do código de hash do seu objeto
	 */
	@Override
	public String toString() {

		return "Nome: " + name + " possuí rg de número: " + rg + " e nasceu no dia: " + dateOfBirth;
	}

}

------

package exerciseone;

public class Application {

	public static void main(String[] args) {
		/*
		 * Na classe Student declaramos um construtor com os campos name, rg e dateOfBirth com isso
		 * eu estou dizendo ao meu programa que minha classe deve ter estes 3 parametros.
		 */
		Student student = new Student("Eduardo Rocha", "50.033.510-2", "25/10/1991" );
		
		// Outra Forma seria setar atributos por atributos passando os valores o resultado é o mesmo.
//		student.name = "Ryube";
//		student.rg = "16.428.041-8";
//		student.dateOfBirth = "20/08/2000";
		
		System.out.println(student);

	}

}

-----

package exercisetwo;

/**
 * Crie as classe Retângulo e implemente os comportamentos área, perímetro,
 * diagonal e volume todos com retorno de dados.
 * 
 * @author Eduardo Rocha
 */
public class Rectangle {
	// attributes
	double width, length, height;

	// Constructor
	public Rectangle(double width, double length, double height) {
		this.width = width;
		this.length = length;
		this.height = height;
	}

	public Rectangle(double width, double length) {
		this.width = width;
		this.length = length;
	}

	public double area() {
		return width * length;
	}

	public double perimetro() {
		return (width * 2) * (length * 2);
	}

	public double diagonal() {
		return width * width + length * length;
	}

	public double volume() {
		return width * length * height;
	}

}

-----

package exercisethree;

/**Crie uma classe que represente um funcionário e realize os testes de funcionalidade. 
 * A classe deve conter os atributos nome, cargo, salário bruto e descontos. 
 * A classe deve prover os seguintes comportamentos: 
 * • Capacidade de realizar o aumento de salário com base em um percentual; • 
 * Calcular o salário líquido; •
 *  Exibir o nome e salário liquido do funcionário.
 *  
 *  @author Eduardo Rocha
*/
public class Employee {
	/**
	 * [NOTA]: Observe que o Java utiliza como convenção a utilização da convenção(Sugestão) camelCase
	 * neste exemplo temos o atributo grossSalary utilizando a convenção, trata-se da primeira palavra ser escrita em 
	 * caixa baixa e as palvras subsequentes por caixa alta, isso facilita a leitura.
	 */
	String name;
	String office;
	Double grossSalary;
	Double discounts;
    Double increase;
    Double netSalary;
	
	double netSalary(double discounts) {
			return 	this.grossSalary - (this.grossSalary * discounts) / 100;
	}
	
	double increaseSalary(double increase) {
		return   this.grossSalary += (this.grossSalary * increase)/100;
	}
	@Override
	public String toString() {
		return "Funcionário: " + name + "\nCargo: " + office + "\nSalário Bruto: " +  grossSalary + " \nDescontos: " + discounts+"%";
	}
	
	
	
	
}

----

package exercisetwo;

public class Application {

	public static void main(String[] args) {

		Rectangle rectangle = new Rectangle(10, 20, 20);
		// Caso deseje adicione um toFixed e limite a quantidade de casas decimais!
		System.out.println("Area é: " + rectangle.area());
		System.out.println("Perimetro é: " + rectangle.perimetro());
		System.out.println("Diagonal é: " + rectangle.diagonal());
		System.out.println("Volume é: " +  rectangle.volume());
		

	}

}

----

package exercisethree;

import java.util.Locale;
import java.util.Scanner;

public class Application {

	public static void main(String[] args) {
		/**
		 * Aqui iremos informa nome, salário, desconto de forma dinâmica ou seja o usuário irá inserir estes valores
		 * e será retornado no final um resumo.
		 * Utilizaremos o Scanner que seria como em C utilizar o scanf e em C++ o cin.
		 */
		
		Scanner sc = new Scanner(System.in); // Com System.in  voc diz a instância de Scanner que ela deve ler os dados de entrada padrão.
		Employee emp = new Employee();
		
		System.out.println("Nome do Funcionário: ");
		emp.name = sc.nextLine();
		System.out.println("Cargo do Funcionário:: ");
		emp.office = sc.nextLine();
		
		System.out.println("Informe o salário bruto: R$ [EX: 800]");
		emp.grossSalary = sc.nextDouble();
		
		System.out.println("Informe desconto: %: [EX: 10] ");
		emp.discounts = sc.nextDouble();
		 
		System.out.println("Informe aumento %: [EX: 10]");
		double increase = sc.nextDouble();
		System.out.println(emp);
		System.out.printf("Salário líquido:  R$ %.2f\n",  emp.netSalary(emp.discounts));
		System.out.println("Aumento de " + increase + "% no salário.");
		System.out.printf("Novo salário bruto com aumento R$ %.2f   \n" , emp.increaseSalary(increase));
	
		

		
	}

}

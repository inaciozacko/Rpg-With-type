import java.util.*;
import java.lang.*;
import java.text.Normalizer;
import java.io.*;

import java.util.Scanner;

public class aa {
	public static int contador = 0;
	public static int contador2 = 1;
	public static int contador3 = 0;
	public static boolean startedPt1 = false;
	public static boolean startedPt2 = false;
	// =====================================

	// FUNCTIONALITIES

	// =====================================
	public static String scan() {
		// função para scan de texto
		Scanner text = new Scanner(System.in);
		return text.nextLine();
	}

	public static void writeDelay(String text, int delay) {
		String[] arr = text.split("");
		String textNow = "";
		for (int x = 0; x < arr.length; x++) {
			int y = x;
			textNow += arr[y];
			Timer(() -> System.out.print(arr[y]), delay * y);
		}
	}
	
	public static void Timer(Runnable runnable, int delay) {

		// Timer for text, beacuse it is hot
		new Thread(() -> {
			try {
				Thread.sleep(delay);
				runnable.run();
			} catch (Exception e) {
				System.err.println(e);
			}
		}).start();
	}

	public static String accent(String str) {
		String[] acentos = { "!", ":", ",", "?", "@", "#", "$", "%", "¨", "&", "*", "(", ")", "[", "]", "{", "}", ".",
				"-", "_", "+", "=" };

		for (int x = 0; x < acentos.length; x++) {
			str = str.replace(acentos[x], "");

		}
		return str;

	}

	public static boolean contains(String a, String b) {
		// função para ver se há algum texto em uma string
		a = accent(a);

		String[] s = a.trim().split(" ");
		for (int i = 0; i < s.length; i++) {
			if (s[i].equals(b)) {
				return true;
			}
		}
		return false;
	}

	public static String Ascii(String string) {
		char[] out = new char[string.length()];
	    string = Normalizer.normalize(string, Normalizer.Form.NFD);
	    int j = 0;
	    for (int i = 0, n = string.length(); i < n; ++i) {
	        char c = string.charAt(i);
	        if (c <= '\u007F') out[j++] = c;
	    }
	    return new String(out);
	}
	// =====================================

	// PART 1:

	// =====================================

	public static String firtPart() {
		String p1 = pt1();

		Scanner sc = new Scanner(System.in);
		
			if (contains(p1, "caixa") && contains(p1, "fosforo") || contains(p1, "fosforo")) {
				String p2 = fosforo1();
				if (contains(p2, "sim") || contains(p2, "Sim")) {
					String p3 = fosforo2();
					String p5 = "";
					if (contains(p3, "sim") || contains(p3, "Sim")) {
						for (; contador2 <= 3; contador2++) {
							System.out.print("Uhmm, não acendeu, tentar novamente?\n->");
							String p4 = scan();
							if (contains(p4, "sim")) {
								contador2 += 1;
							} else if (contains(p4, "não") || contains(p4, "nao")) {
								main(null);
								return null;
							}
						}
						//Aqui começa a parte 2
						String p4 = "";
						p5 = pt2();
						if(contains (p5, "Madeira") || contains(p5, "madeira")) {
							wood();
							if(contains (p4, "Sim") || contains (p4, "sim")) {
								wood2();
								return pt2();
							}
						}else if (contains (p5, "Roupa") || contains(p5, "roupa")) {
							Timer(() -> writeDelay("Em sua gola está escrito: Em volta de sua gola, uma frase escrita “Um lampião, uma lâmpada”\n->", 35), 1);
							String p7 = scan();
							if(contains(p7, "Sim") || contains(p7, "sim")) {
								clothes2();
								return pt2();
							}
						}else if (contains (p5, "porta") || contains(p5, "Porta")) {
							System.out.println("Você não pode fazer isso agora");
							pt2();
							}else if(contains( p5, "visto") || contains( p5, "Visto") || contains( p5, "visto") && contains( p5, "roupa") || contains( p5, "Visto") && contains( p5, " a roupa")) {
								System.out.println("aaaa");
						}
						//========================
					} else {
					 main(null);
					 return null;
					}
				}else {
					main(null);
					 return null;
				}
			}else if(contains(p1, "Roupa") || (contains(p1, "roupa") || contains(p1, "esfarrapada") || contains(p1,  "Esfarrapada")) || (contains(p1, "roupa") && contains(p1, "esfarrapada") || (contains(p1, "Roupa") && contains(p1, "Esfarrapada")))) {
				Timer(() -> writeDelay("Não parece servir em você, talvez esteja um pouco gordo pra ela, mas estão molhadas de qualquer jeito… Parece ter algo escrito, mas está muito escuro para ler.", 35), 1);
				Timer(() -> main(null), 3000);
				return null;
			}else if(contains(p1, "pedaço") || (contains(p1, "pedaco") || contains(p1, "madeira") || contains(p1,  "Madeira")) ||(contains(p1, "pedaço") && contains(p1, "madeira")) || (contains(p1, "pedaco") && contains(p1, "madeira"))) {
				Timer(() -> writeDelay("Um pedaço podre, você até pensa em usar como arma, mas só iria te atrapalhar... Parece ter algo escrito, mas está muito escuro para ler.\n", 35), 10);
				Timer(() -> main(null), 3000);
				return null;
			}else if(contains (p1, "embora") || contains(p1, "casa")|| contains(p1, "saio") || contains(p1, "saio") && contains(p1, "daqui") || contains(p1, "saio") && contains(p1, "desse lugar")) {
				Timer(() -> writeDelay("Não posso recuar agora... cheguei tão longe, fiz tanta coisa, não é agora que vou recuar.\n", 35), 10);
				Timer(() -> main(null), 3000);
				return null;
			}
				return p1;
			}
	

	public static String pt1() {
//		 Firt part (primary lore)
		int delayStarted = 0;
		if (!startedPt1) {
			Timer(() -> writeDelay("Muitas perguntas surgem em sua cabeça ao acordar… ", 35), 1);
			Timer(() -> writeDelay(
					"Você não enxerga nada e a primeira coisa que vem em sua cabeça é que você não deveria ter \naceitado se arriscar desse jeito, sua cabeça doi. Em pouco tempo seus olhos começam a se acostumar com a escuridão, e ",
					35), 4500);
			delayStarted = 12000;
		}
		startedPt1 = true;

		Timer(() -> writeDelay(
				" \nna sua frente você apenas vê: ",35), 2700 + delayStarted);
		Timer(() -> writeDelay("\n- Um pedaço de madeira", 35), 4000 + delayStarted);
		Timer(() -> writeDelay("\n- Roupa esfarrapada", 35), 5000 + delayStarted);
		Timer(() -> writeDelay("\n- E uma caixa de fósforo\nO que você faz?", 35), 6000 + delayStarted);
		Timer(() -> writeDelay("\n->:", 35), 7500 + delayStarted);

		String p1 = scan();
		p1 = Ascii(p1);
		return p1;
	}

	public static String fosforo1() {

		// Part phosphor (The correct choice)
		Timer(() -> writeDelay(
				"Uma pequena caixinha de fósforo, isso te lembra que talvez tenha deixado seu forno ligado... (investiga-lá?)\n->",
				35), 100);

		String p2 = scan();
		p2 = Ascii(p2);
		return p2;
	}

	public static String fosforo2() {
		// Part 2, if player continue whith codigos
		Timer(() -> writeDelay("Uma caixa velha \n",
				35), 5);
		Timer(() -> writeDelay("Aparentemente há como acende-lo... Tentar?\n->", 35), 1500);
		String p3 = scan();
		p3 = Ascii(p3);
		return p3;
	}
	
	//=====================================
	
	//PART 2:
	
	//=====================================

	public static String pt2(){
		int delayStarted = 0;
		if (!startedPt2) {
			Timer(() -> writeDelay("Agora você tem um fosforo aceso! Vendo melhor, nela está escrita “Uhm, isso me lembra um velho ditado de uma sala…”\nEnxergando melhor a sala, ", 35), 1);
			delayStarted = 2000;
		}
		startedPt2 = true;
		
		Timer(() -> writeDelay(
				"você vê:\n",
				35), 3500+delayStarted);
		
		Timer(() -> writeDelay(
				"- Uma roupa esfarrapada\n",
				35), 5000+delayStarted);
		
		Timer(() -> writeDelay(
				"- E uma enorme porta\n",
				35), 6500+delayStarted);
		
		Timer(() -> writeDelay(
				"- Um pedaço de madeira\nO que você faz?\n",
				35), 7500+delayStarted);
		
		
		Timer(() -> writeDelay(
				"->",
				15), 9000+delayStarted);
		
		String p5 = scan();
		p5  = Ascii(p5);
		return p5;
	}
	
	public static String wood() {
		Timer(() -> writeDelay("Um pedaço de madeira úmido, não parece ser tão útil (investigar?)\n->", 35), 1);
		String p4 = scan();
		return p4;
	}
	
	public static String wood2() {
		Timer(() -> writeDelay("Tem um texto escrito... “pequena e escura contendo:”\n", 35), 1);
		
		String p5 = "";
		return p5;
	}	

	public static String clothes2() {
		Timer(() -> writeDelay("Em volta de sua gola, uma frase escrita “Um lampião, uma lâmpada”\n", 35),1);
		String p9 = "";
		return p9;
	}
	
public static void Pt2(String[] args) {
		pt2();
	}
	// =====================================
	public static void main(String[] args) {
		// main function
		firtPart();
	}
}

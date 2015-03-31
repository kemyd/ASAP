# ASAP

 Język programowania przeznaczony dla pracowników agencji reklamowych i PR. Nazwa ma podkreślić szybkość działania. Język skrótowo nazywany **A**, co w alfabetycznym rankingu stawia go na pewnym pierwszym miejscu przed B, C, C++, C#, D, E, oraz F#.


### 1. ASAP jest językiem obiektowym

  
Do tworzenia nowego typu danych używamy **brief**-ów. Brief zawiera listę właściwości oraz features.

	brief Biurowiec:
		
		nazwa  = "X2"
		adres  = "Czerska 12" 			
		piętra = 4
    		
		fyi wolneBiurka = 750		
		
* Właściwości poprzedzone **fyi** są wyłącznie do użycia w danym briefie, nie można ich używać na "zewnątrz". Profesjonalnie nazywa się to hermetyzacją lub enkapsulacją (nazwa spotykana w książkach, rzadziej w mailach).

* Aby zacząć korzystać z briefu należy przekazać go do realizacji. Można to zrobić na dwa sposoby:

		realizacja1 = newbusiness Biurowiec

	lub w skróconej wersji

		realizacja2 = new Biurowiec
		
		
### 2. Briefy można rozszerzać o features

Feature informuje o tym co w ramach briefu możemy robić.		
<pre>
brief Biurowiec:

	fyi wolneBiurka = 750

	<b>feature</b> sprawdzWolneMiejsceDlaLudzika:
    
		challenge wolneBiurka == 0:
			feedback "Nie ma miejsca dla ludzika :("
        
		feedback "Mamy miejsce dla ludzika :)"
</pre>    

* Kod zawarty w instrukcji **challenge** wykona się wyłącznie gdy wynik "czelendżu" będzie zgodny z podanym warunkiem (w powyższym przykładzie gdy nie będzie wolnych biurek). Wcięcia określają bloki kodu.
 
* Jeśli chcemy przerwać działanie **feature** i przekazać dalej informację o tym z jakim rezultatem zakończyło się jego wywołanie powinniśmy użyć instrukcji **feedback**. 

* **Feature** może mieć kilka instrukcji **feedback** (jak wyżej), wybieranych np. na podstawie wyników wywołań innych ficzerów!

### 3. ASAP ma wbudowaną obsługę fuck-upów

Podczas działania programu, tak jak w życiu, mogą wystąpić sytuacje specjalne, do których trzeba podejść w odpowiedni sposób.

	feature sprawdzWolneMiejsceDlaLudzika:
    
		challenge wolneBiurka > 0:
			feedback "Mamy miejsce dla ludzika :)"
    
		next-step wolneBiurka == 0:
        	feedback "Nie ma miejsca dla ludzika :("
        	
		next-step wolneBiurka < 0:
			FUCK-UP "Brak miejsc i to poważny bo ujemny!"

Liczba wolnych biurek mniejsza od 0 jest taką sytuacją. Jej wystąpienie dziwi i na pewno przerywa normalny tok pracy [programu].

Wywołanie powyższego kodu mogłoby wyglądać w następujący sposób:

	risk:	   		
   		dodajLudzika()
   		
	noFun powód:
		imho "Coś się zepsuło" + powód	
	
	
Powyższy kod próbuje wywołać ryzykowną operację. W przypadku zgłoszenia **fuck-up**u w bloku **noFun** zostanie zwrócony jego powód. Polecenie **imho** nieśmiało wysyła podany komunikat na standardowy strumień wyjścia, np. ekran.

### 4. Używanie pętli

**ASAP** jak każdy prawdziwy język programowania posiada obsługę pętli. Jeśli zachodzi potrzeba wykonania bloku kodu określoną ilość razy użyj instrukcji **KPI**:

	wolneBiurka = 750
	
	KPI wolneBiurka == 0:
		dodajLudzika()
		wolneBiurka = wolneBiurka - 1

W powyższym przykładzie instrukcja **dodajLudzika** będzie wywoływana do czasu aż przyjęte "kejpiaje" nie zostaną spełnione (pełne biuro).

Powtarzanie bloku kodu w instrukcji KPI można zakończyć w dowolnym momencie poleceniem **deadline**:

<pre>
wolneBiurka = 750
	
KPI wolneBiurka == 0:

	challenge wolneBiurka == 666:
		imho "szatanista?"
		<b>deadline</b>

	dodajLudzika()
	wolneBiurka = wolneBiurka - 1
</pre>


### 5. Instalacja


	git clone https://github.com/kemyd/ASAP.git
	cd ASAP
	./configure
	
** Oprogramowanie Open and Empty Source udostępnione na licencji KIT. **

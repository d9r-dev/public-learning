- **The Psychology and Economics of Software Testing:**
-
- ## **The Psychology of Testing**
	- Meisten Programmierer haben falsche Definition von Testing "demonstrating that errors are not
	     present" etc.
	- "When you test a program you want to add some value to it. Adding value through testing means
	     raising the quality or reliability of the program. Raising the reliability of the program means finding and removing errors."
	- Ausgangspunkt sollte die Annahme sein, dass ein Programm Fehler enthält (was fast immer der Fall
	     ist) und man diese Fehler finden will.
	- "Testing is the process of executing a program with the intent of finding errors."
	- Richtige Zielsetzung ist ein wichtiger psychologischer Faktor, denn Menschen sind Zielorientiert.
	     Beeinflusst bspw. Die Auswahl der Testdaten
	- "Testing is a destructive, even sadistic, process, which explains why most people find it difficult."
	- Ein "erfolgreicher" Test ist ein Test, der Fehler gefunden hat.
-
- ## The Economics of Testing
	- Es ist unmöglich alle Fehler eines Programms zu finden
	- Selbst triviale Programme haben eine hohe Anzahl von möglichen Inputs und Output Kombinationen
- ### Black-Box-Testing
	- Programm als Black-Box betrachten und keine Annahmen über die Implementierung treffen
	- Kriterium: exhaustive input testing
	- Bei einem Programm dass bestimmt of ein Dreieck gleichschenklig ist gibt es Milliarden Inputkombinationen, man müsste alle möglichen Kombinationen bis zur Intergergrenze der Programmiersprache testen (wer sagt, dass es nicht eine extra Regel im Programm gibt, die das Dreieck 3824,3824,3824 nicht als gleichschenklig bestimmt?)
	- Man müsste nicht nur alle validen Inputs testen, sondern auch alle invaliden --> vollständiger Test ist unmöglich
	- You annot test a programm to guarantee that it is error free
	- A fundamental consideration in program testing is one of economics.
- ### White-Box-Testing (logic-driven testing)
	- Exhausting path testing
	- Jeden möglichen Programmpfad testen
	- Bsp: Ein Programm mit ca. 20 Zeilen und einen Do-Loop, der bis zu 20 mal iteriert, hätte 10hoch14
	  mögliche Pfade, 10 trillionen, bei einem Test alle 5 Minuten würde es 1 Milliarde Jahre dauern das zu testen, ein Test pro Sekunde 3,2 Millionen Jahre
	- Programm könnte alle path tests bestehen und trotzdem nicht der Spezifikation entsprechen
	- Es könnten Pfade fehlen
	-
- ## Software Testing Principles:
	- A necessary part of a test case is a definition of the expected output or result.
	- A programmer should avoid attempting to test his or her own program.
	- A programming organization should not test its own program.
	- Any testing process should include a thorough inspection of the results of each test.
	- Test cases must be written for input conditions that are valid and unexpected, as well as for those
	  that are valid and expected.
	- Examining a program to see if it does not do what is is supposed to do is only half the battle; the other half is seeing whether the program does what it is not supposed to do.
	- Avoid throwaway test cases unless the program is truly a throwaway program.
	- Do not plan a testing effort under the tacit assumption that no errors will be found.
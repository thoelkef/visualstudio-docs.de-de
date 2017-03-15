---
title: "Regelsatz f&#252;r gemischte empfohlene Mindestregeln | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3186b5b-0149-4a75-826e-e3539e4e703f
caps.latest.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 3
---
# Regelsatz f&#252;r gemischte empfohlene Mindestregeln
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kombinierte Microsoft die empfohlene Regelfokus auf dem meisten allgemeinen und wichtige Probleme im C\+\+ 2010\-Projekten, die Common Language Runtime, darunter potenzielle Sicherheitslücken, Anwendung abstürzt und andere wichtige Logik\- und Entwurfsfehler unterstützen.  Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre C\+\+\-Projekte mit Common Language Runtime\-Unterstützung erstellen.  Dieser Regelsatz ist für die Konfiguration mit Visual Studio Professional Edition und höher vorgesehen.  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[C6001](../code-quality/c6001.md)|Nicht initialisierter Speicher wird verwendet|  
|[C6011](../code-quality/c6011.md)|Dereferenzierender NULL\-Zeiger.|  
|[C6029](../code-quality/c6029.md)|Verwendung von ungeprüftem Wert|  
|[C6031](../code-quality/c6031.md)|Rückgabewert wird ignoriert|  
|[C6053](../code-quality/c6053.md)|0 \(null\)\-Abbruch des Aufrufs|  
|[C6054](../code-quality/c6054.md)|0 \(null\)\-Abbruch fehlt|  
|[C6059](../code-quality/c6059.md)|Fehlerhafte Verkettung|  
|[C6063](../code-quality/c6063.md)|Fehlendes Zeichenfolgenargument für Formatfunktion|  
|[C6064](../code-quality/c6064.md)|Fehlendes Ganzzahlargument für Formatfunktion|  
|[C6066](../code-quality/c6066.md)|Fehlendes Zeigerargument für Formatfunktion|  
|[C6067](../code-quality/c6067.md)|Fehlendes Zeichenfolgenzeigerargument für Formatfunktion|  
|[C6101](../code-quality/c6101.md)|Rückgabe von nicht initialisiertem Speicher|  
|[C6200](../code-quality/c6200.md)|Index überschreitet maximale Puffergröße|  
|[C6201](../code-quality/c6201.md)|Index überschreitet maximale Puffergröße|  
|[C6214](../code-quality/c6214.md)|Ungültige Umwandlung von HRESULT in BOOL|  
|[C6215](../code-quality/c6215.md)|Ungültige Umwandlung von BOOL in HRESULT|  
|[C6216](../code-quality/c6216.md)|Ungültige, vom Compiler eingefügte Umwandlung von BOOL in HRESULT|  
|[C6217](../code-quality/c6217.md)|Ungültiger HRESULT\-Test mit NOT|  
|[C6220](../code-quality/c6220.md)|Ungültiges HRESULT vergleicht bis \-1|  
|[C6226](../code-quality/c6226.md)|Ungültige HRESULT\-Zuweisung bis \-1|  
|[C6230](../code-quality/c6230.md)|Ungültige HRESULT\-Verwendung als boolescher Wert|  
|[C6235](../code-quality/c6235.md)|Konstante ungleich 0 \(null\) mit Logisch\-oder|  
|[C6236](../code-quality/c6236.md)|Logisch\- oder mit Konstante ungleich 0 \(null\)|  
|[C6237](../code-quality/c6237.md)|Null mit logischem Außerdem verliert Nebeneffekte|  
|[C6242](../code-quality/c6242.md)|Lokale Entladung erzwungen|  
|[C6248](../code-quality/c6248.md)|Erstelle NULL\-DACL|  
|[C6250](../code-quality/c6250.md)|Nicht veröffentlichte Adressdeskriptoren|  
|[C6255](../code-quality/c6255.md)|Ungeschützte Verwendung von 'alloca'|  
|[C6258](../code-quality/c6258.md)|Verwenden beenden Sie Threads|  
|[C6259](../code-quality/c6259.md)|Code in Toter bitweise OR\- eingeschränktem Schalter|  
|[C6260](../code-quality/c6260.md)|Verwendung von Byte\-Arithmetik|  
|[C6262](../code-quality/c6262.md)|Übermäßige Stapelverwendung|  
|[C6263](../code-quality/c6263.md)|alloca' wird in Schleife verwendet|  
|[C6268](../code-quality/c6268.md)|Fehlende Klammern in Umwandlung|  
|[C6269](../code-quality/c6269.md)|Zeiger\-Dereferenzierung wurde ignoriert|  
|[C6270](../code-quality/c6270.md)|Fehlendes Gleitkommaargument für Formatfunktion|  
|[C6271](../code-quality/c6271.md)|Zusätzliches Argument für Formatfunktion|  
|[C6272](../code-quality/c6272.md)|Nicht\-Gleitkommaargument für Formatfunktion|  
|[C6273](../code-quality/c6273.md)|Nicht ganze Argumen, um von Funktion zu formatieren|  
|[C6274](../code-quality/c6274.md)|Nicht\-Zeichenargument für Formatfunktion|  
|[C6276](../code-quality/c6276.md)|Ungültige Zeichenfolgenumwandlung|  
|[C6277](../code-quality/c6277.md)|Ungültiger CreateProcess\-Aufruf|  
|[C6278](../code-quality/c6278.md)|Keine Übereinstimmung zwischen "New"\-Arrayoperator und "Delete"\-Skalaroperator|  
|[C6279](../code-quality/c6279.md)|Keine Übereinstimmung zwischen "New"\-Skalaroperator und "Delete"\-Arrayoperator|  
|[C6280](../code-quality/c6280.md)|Keine Übereinstimmung zwischen SpeicherSpeicherbelegung und Aufheben der Speicherbelegung|  
|[C6281](../code-quality/c6281.md)|Bitweiser Relationsvorrang|  
|[C6282](../code-quality/c6282.md)|Zuweisung ersetzt Test|  
|[C6283](../code-quality/c6283.md)|Keine Übereinstimmung zwischen primitivem "New"\-Arrayoperator und "Delete"\-Skalaroperator|  
|[C6284](../code-quality/c6284.md)|Ungültiges Objekt\-Argument für Formatfunktion|  
|[C6285](../code-quality/c6285.md)|Logisch\- oder von Konstanten|  
|[C6286](../code-quality/c6286.md)|Logisch\- oder Zeitabstände Nebeneffekte ungleich 0 \(null\)|  
|[C6287](../code-quality/c6287.md)|Redundanter Test|  
|[C6288](../code-quality/c6288.md)|Gegenseitige Einschluss über logischem Und ist falsch|  
|[C6289](../code-quality/c6289.md)|Mit gegenseitigem Ausschluss über Logisch\- oder gilt|  
|[C6290](../code-quality/c6290.md)|Logisches NOT Bitweis\- und Rangfolge|  
|[C6291](../code-quality/c6291.md)|Rangfolge des bitweisen OR des logischen Nicht|  
|[C6292](../code-quality/c6292.md)|Schleife zählt vom Maximum nach oben|  
|[C6293](../code-quality/c6293.md)|Schleife zählt vom Minimum nach unten|  
|[C6294](../code-quality/c6294.md)|Schleifentext wurde niemals ausgeführt|  
|[C6295](../code-quality/c6295.md)|Unendliche Schleife|  
|[C6296](../code-quality/c6296.md)|Schleife wird nur einmal ausgeführt|  
|[C6297](../code-quality/c6297.md)|Ergebnis der "Shift"\-Umwandlung \(Vergrößerung\)|  
|[C6299](../code-quality/c6299.md)|Bitfeld zu booleschem Vergleich|  
|[C6302](../code-quality/c6302.md)|Ungültiges Zeichenfolgenargument für Formatfunktion|  
|[C6303](../code-quality/c6303.md)|Ungültiges Zeichenfolgenargument für breite Zeichen zu Formatfunktion|  
|[C6305](../code-quality/c6305.md)|Keine Übereinstimmung bei Größe und Count\-Verwendung|  
|[C6306](../code-quality/c6306.md)|Falscher Variablenargument\-Funktionsaufruf|  
|[C6308](../code-quality/c6308.md)|Verlust neu zuweisen|  
|[C6310](../code-quality/c6310.md)|Unzulässige Ausnahme in Filterkonstante|  
|[C6312](../code-quality/c6312.md)|Ausnahme Ausführungsschleife fortsetzen|  
|[C6314](../code-quality/c6314.md)|Rangfolge des bitweisen OR|  
|[C6317](../code-quality/c6317.md)|Nicht nicht Ergänzen|  
|[C6318](../code-quality/c6318.md)|Ausnahme Suche Fortsetzen|  
|[C6319](../code-quality/c6319.md)|Wird durch Kommata ignoriert|  
|[C6324](../code-quality/c6324.md)|Zeichenfolgenkopie statt Zeichenfolgenvergleich|  
|[C6328](../code-quality/c6328.md)|Möglicher Argumenttypenkonflikt|  
|[C6331](../code-quality/c6331.md)|Ungültige VirtualFree\-Flags|  
|[C6332](../code-quality/c6332.md)|Ungültiger VirtualFree\-Parameter|  
|[C6333](../code-quality/c6333.md)|Ungültige VirtualFree\-Size|  
|[C6335](../code-quality/c6335.md)|Verlust in Prozesshandle|  
|[C6381](../code-quality/c6381.md)|Information zum Herunterfahren fehlt|  
|[C6383](../code-quality/c6383.md)|Element\-Anzahl Byte\-Anzahl Pufferüberlauf|  
|[C6384](../code-quality/c6384.md)|Zeigergrößen\-Division|  
|[C6385](../code-quality/c6385.md)|Leseüberlauf|  
|[C6386](../code-quality/c6386.md)|Schreibüberlauf|  
|[C6387](../code-quality/c6387.md)|Ungültiger Parameterwert|  
|[C6388](../code-quality/c6388.md)|Ungültiger Parameterwert|  
|[C6500](../code-quality/c6500.md)|Ungültige Attributeigenschaft|  
|[C6501](../code-quality/c6501.md)|In Konflikt stehende Attributeigenschaftswerte|  
|[C6503](../code-quality/c6503.md)|Verweise dürfen nicht NULL sein.|  
|[C6504](../code-quality/c6504.md)|NULL auf Nichtzeiger|  
|[C6505](../code-quality/c6505.md)|MustCheck für "void"|  
|[C6506](../code-quality/c6506.md)|Puffergröße auf Nichtzeiger oder Array|  
|[C6507](http://msdn.microsoft.com/de-de/18f88cd1-d035-4403-a6a4-12dd0affcf21)|Ungültiger Konflikt an Nullen Dereferenzierung|  
|[C6508](../code-quality/c6508.md)|Schreibzugriff auf Konstante|  
|[C6509](../code-quality/c6509.md)|Rückgabe wurde für Vorbedingung verwendet|  
|[C6510](../code-quality/c6510.md)|NULL für Nichtzeiger abgebrochen|  
|[C6511](../code-quality/c6511.md)|MustCheck Muss "Ja" oder "Nein" lauten|  
|[C6513](../code-quality/c6513.md)|Elementgröße ohne Puffergröße|  
|[C6514](../code-quality/c6514.md)|Puffergröße übersteigt Arraygröße|  
|[C6515](../code-quality/c6515.md)|Puffergröße auf Nichtzeiger|  
|[C6516](../code-quality/c6516.md)|Keine Eigenschaften für Attribut|  
|[C6517](../code-quality/c6517.md)|Zulässige Größe für nicht lesbaren Puffer|  
|[C6518](../code-quality/c6518.md)|Schreibbare Größe für Puffer, der nicht geschrieben werden kann|  
|[C6519](http://msdn.microsoft.com/de-de/2b6326b0-0539-4d26-8fb1-720114933232)|Ungültige Anmerkung: Wert der Eigenschaft "NeedsRelease" muss Yes oder No sein|  
|[C6521](http://msdn.microsoft.com/de-de/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|Ungültige Größen\-Zeichenfolge Dereferenzierung|  
|[C6522](../code-quality/c6522.md)|Ungültiger Größenzeichenfolgentyp|  
|[C6523](http://msdn.microsoft.com/de-de/11397a31-b224-46b0-afb7-d49ca576a3bb)|Ungültiger Größen\-Zeichenfolgen\-Parameter|  
|[C6525](../code-quality/c6525.md)|Ungültiger Größenzeichenfolgenstandort|  
|[C6526](http://msdn.microsoft.com/de-de/59c590c7-0098-4166-a1ac-87f324596002)|Ungültiger Größen\-Zeichenfolgen\-Puffer\-Typ|  
|[C6527](../code-quality/c6527.md)|Ungültige Anmerkung: Eigenschaft "NeedsRelease" darf nicht für Werte vom Typ void verwendet werden|  
|[C6530](../code-quality/c6530.md)|Unbekannter Formatzeichenfolgenstil|  
|[C6540](../code-quality/c6540.md)|Die Verwendung von Attributanmerkungen auf diese Funktion werden alle seine vorhandenen \_\_declspec Anmerkungen ungültig|  
|[C6551](../code-quality/c6551.md)|Ungültige Größenangabe: Ausdruck nicht parsable|  
|[C6552](../code-quality/c6552.md)|Ungültiges Deref\= oder Notref\=: Ausdruck nicht parsable|  
|[C6701](../code-quality/c6701.md)|Der Wert, ein gültiges ja\/nein\/nicht ausgewertet werden|  
|[C6702](../code-quality/c6702.md)|Der Wert ist kein Zeichenfolgenwert|  
|[C6703](../code-quality/c6703.md)|Der Wert ist keine Zahl|  
|[C6704](../code-quality/c6704.md)|Unerwarteter Anmerkungs\-Ausdrucks\-Fehler|  
|[C6705](../code-quality/c6705.md)|Erwartete Zahl Argumente für Anmerkungen stimmt nicht tatsächliche Anzahl Argumente für Anmerkungen ab|  
|[C6706](../code-quality/c6706.md)|Unerwarteter Anmerkungs\-Fehler für Anmerkungen|  
|[C6995](../code-quality/c6995.md)|Fehler beim Speichern der XML\-Protokolldatei.|  
|[C26100](../code-quality/c26100.md)|Racebedingung|  
|[C26101](../code-quality/c26101.md)|Fehler bei der ordnungsgemäßen Verwendung des ineinandergreifenden Vorgangs|  
|[C26110](../code-quality/c26110.md)|Fehler des Aufrufers beim Aufrechterhalten der Sperre|  
|[C26111](../code-quality/c26111.md)|Fehler des Aufrufers beim Lösen der Sperre|  
|[C26112](../code-quality/c26112.md)|Aufrechterhalten von Sperren durch Aufrufer nicht möglich|  
|[C26115](../code-quality/c26115.md)|Lösen der Sperre fehlgeschlagen|  
|[C26116](../code-quality/c26116.md)|Einrichtung oder Aufrechterhaltung der Sperre fehlgeschlagen|  
|[C26117](../code-quality/c26117.md)|Nicht gehaltene Sperre wird gelöst|  
|[C26140](../code-quality/c26140.md)|Nebenläufigkeitsfehler bei SAL\-Anmerkung.|  
|[C28020](../code-quality/c28020.md)|Der Ausdruck ist bei diesem Aufruf nicht "True".|  
|[C28021](../code-quality/c28021.md)|Der mit einer Anmerkung zu versehende Parameter muss ein Zeiger sein.|  
|[C28022](../code-quality/c28022.md)|Die Funktionsklassen auf diese Funktion nicht die gleichen Funktionsklasse auf der Typedef ab, die verwendet wird, um sie zu definieren.|  
|[C28023](../code-quality/c28023.md)|Die zuweisende oder übergebene Funktion sollte eine \_Function\_class\_ Anmerkung für eine der Klasse mindestens|  
|[C28024](../code-quality/c28024.md)|Der Funktionszeiger, der zugeordnet wird, wird mit der Funktionsklasse gekennzeichnet, die nicht in der Funktionsklassenliste enthalten ist.|  
|[C28039](../code-quality/c28039.md)|Der Typ des tatsächlichen Parameters sollte genau mit dem Typ übereinstimmen.|  
|[C28112](../code-quality/c28112.md)|Auf eine Variable, auf die über einer gesperrten Funktion zugegriffen wird, muss über einer gesperrten Funktion immer zugreifen.|  
|[C28113](../code-quality/c28113.md)|Zugriff auf eine lokale Variable über eine Interlocked\-Funktion|  
|[C28125](../code-quality/c28125.md)|Die Funktion muss innerhalb eines try\/except\-Blocks aufgerufen werden.|  
|[C28137](../code-quality/c28137.md)|Das Variablenargument sollte Konstante eine \(Literal\) sein|  
|[C28138](../code-quality/c28138.md)|Das konstante Argument sollte stattdessen variabel sein.|  
|[C28159](../code-quality/c28159.md)|Erwägen Sie, stattdessen eine andere Funktion zu verwenden.|  
|[C28160](../code-quality/c28160.md)|Fehleranmerkung|  
|[C28163](../code-quality/c28163.md)|Die Funktion sollte nie innerhalb eines try\/except\-Blocks aufgerufen werden.|  
|[C28164](../code-quality/c28164.md)|Das Argument wird an eine Funktion übergeben, die einen Zeiger auf ein Objekt erwartet \(kein Zeiger auf Zeiger\)|  
|[C28182](../code-quality/c28182.md)|Dereferenzierender NULL\-Zeiger.  Der Mauszeiger enthält dieselben NULL\-Wert, den einem anderen Zeiger geladen.|  
|[C28183](../code-quality/c28183.md)|Das Argument könnte ein Wert sein und ist eine Kopie des im Zeiger enthaltenen Werts.|  
|[C28193](../code-quality/c28193.md)|Die Variable enthält einen Wert, der überprüft werden muss|  
|[C28196](../code-quality/c28196.md)|Die Anforderung ist nicht erfüllt. \(Der Ausdruck wird nicht mit "True" ausgewertet.\)|  
|[C28202](../code-quality/c28202.md)|Illegaler Verweis auf nicht statischen Member.|  
|[C28203](../code-quality/c28203.md)|Mehrdeutiger Verweis auf Klassenmember.|  
|[C28205](../code-quality/c28205.md)|\_Success\_ oder \_On\_failure\_ verwendet in einem ungültigen Kontext|  
|[C28206](../code-quality/c28206.md)|Linker Operand zeigt auf eine Struktur, mit "\-\>"|  
|[C28207](../code-quality/c28207.md)|Linker Operand ist eine Struktur, mit "."|  
|[C28209](../code-quality/c28209.md)|Die Deklaration für das Symbol weist einen Konflikt auf.|  
|[C28210](../code-quality/c28210.md)|Anmerkungen für den \_\_on\_failure Kontext dürfen nicht explizit Kontext vor sein|  
|[C28211](../code-quality/c28211.md)|Statischer Kontextname erwartet für SAL\_context|  
|[C28212](../code-quality/c28212.md)|Zeigerausdruck für Anmerkung erwartet|  
|[C28213](../code-quality/c28213.md)|Die \_Use\_decl\_annotations\_\-Anmerkung muss ohne Änderung zum Verweisen auf eine vorherige Deklaration verwendet werden.|  
|[C28214](../code-quality/c28214.md)|Attributparameternamen müssen p1...p9 sein.|  
|[C28215](../code-quality/c28215.md)|Der Typefix kann nicht auf einen Parameter angewendet werden, der bereits über einen Typefix verfügt.|  
|[C28216](../code-quality/c28216.md)|Die checkReturn Anmerkung gilt nur für Nachbedingungen für Funktionsparameter bestimmten zu.|  
|[C28217](../code-quality/c28217.md)|Eine Funktion stimmt die Anzahl der Parameter für Anmerkungen nicht die ab, die an der Datei gefunden wird|  
|[C28218](../code-quality/c28218.md)|Für paramteer Funktion stimmt der Parameter der Anmerkung nicht den ab, der die Datei gefunden wird|  
|[C28219](../code-quality/c28219.md)|Member von Enumeration für den Parameter in der Anmerkung erwartet|  
|[C28220](../code-quality/c28220.md)|Ganzzahliger Ausdruck erwartet für Anmerkungen den Parameter in der Anmerkung|  
|[C28221](../code-quality/c28221.md)|Zeichenfolgenausdruck für den Parameter in der Anmerkung erwartet|  
|[C28222](../code-quality/c28222.md)|\_\_yes, \_\_no oder \_\_maybe erwartet für Anmerkungen|  
|[C28223](../code-quality/c28223.md)|Hat nicht erwartet Token\/Bezeichner für Anmerkungen, Parameter|  
|[C28224](../code-quality/c28224.md)|Anmerkung erfordert Parameter|  
|[C28225](../code-quality/c28225.md)|Hat nicht die richtige Anzahl erforderlicher Parameter in der Anmerkung|  
|[C28226](../code-quality/c28226.md)|Anmerkung kann nicht zusätzlich ein PrimOp sein \(in der aktuellen Deklaration\).|  
|[C28227](../code-quality/c28227.md)|Anmerkung kann nicht zusätzlich ein PrimOp sein \(siehe vorherige Deklaration\).|  
|[C28228](../code-quality/c28228.md)|Anmerkungsparameter: kann nicht Typ verwenden Anmerkungen|  
|[C28229](../code-quality/c28229.md)|Anmerkung unterstützt keine Parameter.|  
|[C28230](../code-quality/c28230.md)|Der Typ des Parameters aufweist keinen Member.|  
|[C28231](../code-quality/c28231.md)|Anmerkung ist nur im Array gültig.|  
|[C28232](../code-quality/c28232.md)|Beitrag vor oder deref angewendet kein Konfigurationsformat Anmerkung|  
|[C28233](../code-quality/c28233.md)|Beitrag vor oder deref angewendete Block|  
|[C28234](../code-quality/c28234.md)|\_\_at Ausdruck gilt nicht auf aktuelle Funktion zu|  
|[C28235](../code-quality/c28235.md)|Die Funktion kann nicht eigenständig als Anmerkung|  
|[C28236](../code-quality/c28236.md)|Die Anmerkung kann nicht in einem Ausdruck verwendet werden|  
|[C28237](../code-quality/c28237.md)|Die Anmerkung auf Parameter wird nicht mehr unterstützt|  
|[C28238](../code-quality/c28238.md)|Die Anmerkung auf Parameter hat mehr als einer von Wert, der stringValue und von longValue.  Verwenden Sie paramn\=xxx.|  
|[C28239](../code-quality/c28239.md)|Die Anmerkung auf Parameter können beide bewerten, stringValue oder longValue; und paramn\=xxx.  Verwenden Sie nur paramn\=xxx.|  
|[C28240](../code-quality/c28240.md)|Die Anmerkung auf Parameter verfügt param2 jedoch kein param1|  
|[C28241](../code-quality/c28241.md)|Die Anmerkung für Funktion auf Parameter wird nicht erkannt|  
|[C28243](../code-quality/c28243.md)|Die Anmerkung für Funktion auf Parameter erfordert mehr dereferenziert, als der eigentliche kommentierte Typ zulässig|  
|[C28244](../code-quality/c28244.md)|Die Anmerkung für Funktion verfügt über einen Parameter unparseable\/eine externe Anmerkung|  
|[C28245](../code-quality/c28245.md)|Die Anmerkung für Funktion kommentiert "this" auf einer Nicht\-MemberFunktion|  
|[C28246](../code-quality/c28246.md)|Die Parameteranmerkung für Funktion stimmt nicht den Typ des Parameters ab|  
|[C28250](../code-quality/c28250.md)|Inkonsistenter Anmerkung für Funktion: die vorherige Instanz hat einen Fehler.|  
|[C28251](../code-quality/c28251.md)|Inkonsistenter Anmerkung für Funktion: diese Instanz hat einen Fehler.|  
|[C28252](../code-quality/c28252.md)|Inkonsistenter Anmerkung für Funktion: Parameter verfügt eine anderen Anmerkungen auf dieser Instanz.|  
|[C28253](../code-quality/c28253.md)|Inkonsistenter Anmerkung für Funktion: Parameter verfügt eine anderen Anmerkungen auf dieser Instanz.|  
|[C28254](../code-quality/c28254.md)|Der Operator dynamic\_cast \<\>\(\) wird i Anmerkungen unterstützt|  
|[C28262](../code-quality/c28262.md)|Ein Syntaxfehler in der Anmerkung wurde in der Funktion, für Anmerkungen gefunden|  
|[C28263](../code-quality/c28263.md)|Ein Syntaxfehler in einer bedingten Anmerkung wurde für systeminterne Anmerkung gefunden|  
|[C28264](http://msdn.microsoft.com/de-de/bf6ea983-a06e-4752-a042-747a7dbf338c)|Ergebnislistenwerte müssen Konstanten sein.|  
|[C28267](../code-quality/c28267.md)|Ein Syntaxfehler in den Anmerkungen war gefundene Anmerkung in der Funktion.|  
|[C28272](../code-quality/c28272.md)|Die Anmerkung für Funktion, Parameter, wenn die Untersuchung mit der Funktionsdeklaration inkonsistent ist|  
|[C28273](../code-quality/c28273.md)|Eine Funktion sind die Anhaltspunkte mit der Funktionsdeklaration steht|  
|[C28275](../code-quality/c28275.md)|Der Parameter für \_Macro\_value\_ ist ungültig|  
|[C28279](../code-quality/c28279.md)|Für Symbol "starten Sie" gefunden ohne ein abgleichendes "Ende"|  
|[C28280](../code-quality/c28280.md)|Für "Symbol wurde ein Ende" gefunden ohne Übereinstimmung "starten"|  
|[C28282](../code-quality/c28282.md)|Formatzeichenfolgen müssen sich in Vorbedingungen befinden.|  
|[C28285](../code-quality/c28285.md)|Eine Funktion Syntaxfehler im Parameter|  
|[C28286](../code-quality/c28286.md)|Eine Funktion Syntaxfehler nahe dem Ende|  
|[C28287](../code-quality/c28287.md)|Eine Funktion Syntaxfehler in \_At\_\(\) Anmerkung \(nicht erkannter Parametername\)|  
|[C28288](../code-quality/c28288.md)|Eine Funktion Syntaxfehler in \_At\_\(\) Anmerkung \(Ungültige Parametername\)|  
|[C28289](../code-quality/c28289.md)|Eine Funktion: ReadableTo oder WritableTo haben eine GrenzeSpezifikation nicht als Parameter|  
|[C28290](../code-quality/c28290.md)|die Anmerkung für Funktion enthält mehr als Externals die tatsächliche Anzahl von Parametern|  
|[C28291](../code-quality/c28291.md)|Beitrag NULL\/notnull auf deref Ebene 0 ist für Funktion ohne Bedeutung.|  
|[C28300](../code-quality/c28300.md)|Ausdrucksoperanden von inkompatiblen Typen für Operator|  
|[C28301](../code-quality/c28301.md)|keine Anmerkungen für erste Deklaration der Funktion.|  
|[C28302](../code-quality/c28302.md)|Ein zusätzlicher \_Deref\_ Operator wurde auf Anmerkung gefunden.|  
|[C28303](../code-quality/c28303.md)|Mehrdeutiger \_Deref\_ Ein Operator wurde auf Anmerkung gefunden.|  
|[C28304](../code-quality/c28304.md)|Ein nicht ordnungsgemäß platzierter \_Notref\_ Operator war zum Token Kontext auf.|  
|[C28305](../code-quality/c28305.md)|Ein Fehler, während des Analysieren eines Tokens ermittelt wurde.|  
|[C28306](../code-quality/c28306.md)|Die Anmerkung auf Parameter ist schwindend|  
|[C28307](../code-quality/c28307.md)|Die Anmerkung auf Parameter ist schwindend|  
|[C28350](../code-quality/c28350.md)|Die Anmerkung beschreibt eine Situation, die bedingt nicht anwendbar ist.|  
|[C28351](../code-quality/c28351.md)|Die Anmerkung beschreibt, wo ein dynamischer Wert \(eine Variable\) nicht in der Bedingung verwendet werden kann.|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Ereignishandler korrekt deklarieren|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Assemblys mit AssemblyVersionAttribute markieren|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden können|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P\/Invokes in NativeMethods\-Klasse verschieben|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Basisklassenmethoden nicht ausblenden|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable korrekt implementieren|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Keine Ausnahmen an unerwarteten Speicherorten auslösen|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Doppelte Zugriffstasten vermeiden|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Für P\/Invoke müssen Einstiegspunkte vorhanden sein.|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P\/Invokes dürfen nicht sichtbar sein.|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typen mit automatischem Layout sollten nicht für COM sichtbar sein|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|GetLastError unmittelbar nach P\/Invoke aufrufen|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Für COM sichtbare Basistypen sollten für COM sichtbar sein|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Die COM\-Registrierungsmethoden müssen übereinstimmen.|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P\/Invokes korrekt deklarieren|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Werttypfelder sollten portabel sein.|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklarationen von P\/Invoke müssen portabel sein.|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Auf Objekten mit schwacher Identität nicht sperren|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL\-Abfragen auf Sicherheitsrisiken überprüfen|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Marshalling für P\/Invoke\-Zeichenfolgenargumente festlegen|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Deklarative Sicherheit auf Werttypen überprüfen|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Zeiger sollten nicht sichtbar sein.|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Gesicherte Typen sollten keine Felder verfügbar machen.|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Methodensicherheit sollte Superset des Typs sein|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA\-Methoden sollten nur APTCA\-Methoden aufrufen|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA\-Typen sollten nur APTCA\-Basistypen erweitern|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Methoden mit Linkaufrufen nicht indirekt verfügbar machen|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Überschreibungslinkaufrufe sollten zur Basis identisch sein|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Anfällige finally\-Klauseln mit äußerem try\-Block umschließen|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typlinkaufrufe erfordern Vererbungsanforderungen|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Sicherheitsrelevante Typen werden möglicherweise nicht an Typäquivalenz beteiligt|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegaten müssen an Methoden mit Transparenz konsistenter binden|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Methoden müssen konsistente Transparenz halten, während sie Basismethoden überschreiben|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparente Methoden müssen nur überprüfbares IL enthalten|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparente Methoden dürfen Methoden mit dem SuppressUnmanagedCodeSecurity\-Attribut nicht aufrufen|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparenter Code darf sicherheitsrelevante Elemente verweisen|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparente Methoden dürfen LinkDemands nicht erfüllen|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen.|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparente Methoden können nicht Sicherheitsassertions|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparente Methoden dürfen nicht in systemeigenen Code aufrufen|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Erneut ausführen, um Stapeldetails beizubehalten|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Objekte nicht mehrmals verwerfen|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Statische Felder für Werttyp inline initialisieren|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|ServicedComponents nicht mit WebMethod markieren|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Überschreibbare Methoden in Konstruktoren nicht aufrufen|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Verwerfbare Typen sollten einen Finalizer deklarieren|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizer sollten Basisklassen\-Finalizer aufrufen|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Serialisierungskonstruktoren implementieren|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Windows Forms\-Einstiegspunkte mit STAThread markieren|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Alle nicht serialisierbaren Felder markieren|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Basisklassenmethoden auf ISerializable\-Typen aufrufen|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable\-Typen mit SerializableAttribute markieren|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Serialisierungsmethoden korrekt implementieren|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable ordnungsgemäß implementieren|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Geben Sie die korrekte Anzahl für Formatierungsmethoden an.|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Ordnungsgemäß auf NaN testen|
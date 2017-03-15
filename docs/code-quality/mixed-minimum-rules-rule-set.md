---
title: "Regelsatz f&#252;r gemischte Mindestregeln | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# Regelsatz f&#252;r gemischte Mindestregeln
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft kombinierte minimale Regeln konzentrieren auf die wichtigsten Probleme im C\+\+ 2010\-Projekten, die Common Language Runtime unterstützen, darunter potenzielle Sicherheitslücken und Abstürze der Anwendung.  Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre C\+\+\-Projekte mit Common Language Runtime\-Unterstützung erstellen.  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[C6001](../code-quality/c6001.md)|Nicht initialisierter Speicher wird verwendet|  
|[C6011](../code-quality/c6011.md)|Dereferenzierender NULL\-Zeiger.|  
|[C6029](../code-quality/c6029.md)|Verwendung von ungeprüftem Wert|  
|[C6053](../code-quality/c6053.md)|0 \(null\)\-Abbruch des Aufrufs|  
|[C6059](../code-quality/c6059.md)|Fehlerhafte Verkettung|  
|[C6063](../code-quality/c6063.md)|Fehlendes Zeichenfolgenargument für Formatfunktion|  
|[C6064](../code-quality/c6064.md)|Fehlendes Ganzzahlargument für Formatfunktion|  
|[C6066](../code-quality/c6066.md)|Fehlendes Zeigerargument für Formatfunktion|  
|[C6067](../code-quality/c6067.md)|Fehlendes Zeichenfolgenzeigerargument für Formatfunktion|  
|[C6101](../code-quality/c6101.md)|Rückgabe von nicht initialisiertem Speicher|  
|[C6200](../code-quality/c6200.md)|Index überschreitet maximale Puffergröße|  
|[C6201](../code-quality/c6201.md)|Index überschreitet maximale Puffergröße|  
|[C6270](../code-quality/c6270.md)|Fehlendes Gleitkommaargument für Formatfunktion|  
|[C6271](../code-quality/c6271.md)|Zusätzliches Argument für Formatfunktion|  
|[C6272](../code-quality/c6272.md)|Nicht\-Gleitkommaargument für Formatfunktion|  
|[C6273](../code-quality/c6273.md)|Nicht ganze Argumen, um von Funktion zu formatieren|  
|[C6274](../code-quality/c6274.md)|Nicht\-Zeichenargument für Formatfunktion|  
|[C6276](../code-quality/c6276.md)|Ungültige Zeichenfolgenumwandlung|  
|[C6277](../code-quality/c6277.md)|Ungültiger CreateProcess\-Aufruf|  
|[C6284](../code-quality/c6284.md)|Ungültiges Objekt\-Argument für Formatfunktion|  
|[C6290](../code-quality/c6290.md)|Logisches NOT Bitweis\- und Rangfolge|  
|[C6291](../code-quality/c6291.md)|Rangfolge des bitweisen OR des logischen Nicht|  
|[C6302](../code-quality/c6302.md)|Ungültiges Zeichenfolgenargument für Formatfunktion|  
|[C6303](../code-quality/c6303.md)|Ungültiges Zeichenfolgenargument für breite Zeichen zu Formatfunktion|  
|[C6305](../code-quality/c6305.md)|Keine Übereinstimmung bei Größe und Count\-Verwendung|  
|[C6306](../code-quality/c6306.md)|Falscher Variablenargument\-Funktionsaufruf|  
|[C6328](../code-quality/c6328.md)|Möglicher Argumenttypenkonflikt|  
|[C6385](../code-quality/c6385.md)|Leseüberlauf|  
|[C6386](../code-quality/c6386.md)|Schreibüberlauf|  
|[C6387](../code-quality/c6387.md)|Ungültiger Parameterwert|  
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
|[C28021](../code-quality/c28021.md)|Der mit einer Anmerkung zu versehende Parameter muss ein Zeiger sein.|  
|[C28182](../code-quality/c28182.md)|Dereferenzierender NULL\-Zeiger.  Der Mauszeiger enthält dieselben NULL\-Wert, den einem anderen Zeiger geladen.|  
|[C28202](../code-quality/c28202.md)|Illegaler Verweis auf nicht statischen Member.|  
|[C28203](../code-quality/c28203.md)|Mehrdeutiger Verweis auf Klassenmember.|  
|[C28205](../code-quality/c28205.md)|\_Success\_ oder \_On\_failure\_ verwendet in einem ungültigen Kontext|  
|[C28206](../code-quality/c28206.md)|Linker Operand zeigt auf eine Struktur, mit "\-\>"|  
|[C28207](../code-quality/c28207.md)|Linker Operand ist eine Struktur, mit "."|  
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
|[C28350](../code-quality/c28350.md)|Die Anmerkung beschreibt eine Situation, die bedingt nicht anwendbar ist.|  
|[C28351](../code-quality/c28351.md)|Die Anmerkung beschreibt, wo ein dynamischer Wert \(eine Variable\) nicht in der Bedingung verwendet werden kann.|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
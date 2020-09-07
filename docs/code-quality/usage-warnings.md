---
title: Verwendungswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd2f5919b0f48290ecc14cf71295e2af0bac4748
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509717"
---
# <a name="usage-warnings"></a>Verwendungswarnungen

Verwendungs Warnungen unterstützen die ordnungsgemäße Verwendung von .net.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1801: Nicht verwendete Parameter überprüfen.](../code-quality/ca1801.md)|Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird.|
|[CA1816: GC.SuppressFinalize korrekt aufrufen.](../code-quality/ca1816.md)|Eine Methode, die eine Implementierung von Dispose bildet, ruft nicht GC.SuppressFinalize auf, oder eine Methode, die keine Implementierung von Dispose bildet, ruft GC.SuppressFinalize auf, oder eine Methode ruft GC.SuppressFinalize auf und übergibt ein anderes Element als dieses (Me in Visual Basic).|
|[CA2200: Erneut ausführen, um Stapeldetails beizubehalten.](../code-quality/ca2200.md)|Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird in der throw-Anweisung explizit angegeben. Wenn eine Ausnahme durch Angeben der Ausnahme in der throw-Anweisung erneut ausgelöst wird, geht die Liste der Methoden, die zwischen der Methode, durch die die Ausnahme ursprünglich ausgelöst wurde, und der aktuellen Methode aufgerufen wurden, verloren.|
|[CA2201: Keine reservierten Ausnahmetypen auslösen.](../code-quality/ca2201.md)|Dadurch wird der ursprüngliche Fehler schwer zu erkennen und zu debuggen.|
|[CA2202: Objekte nicht mehrmals verwerfen.](../code-quality/ca2202.md)|Eine Methodenimplementierung enthält Codepfade, die für dasselbe Objekt mehrere Aufrufe von System.IDisposable.Dispose oder einer Entsprechung von Dispose (z. B. einer Close()-Methode für bestimmte Typen) verursachen können.|
|[CA2207: Statische Felder für Werttyp inline initialisieren.](../code-quality/ca2207.md)|Ein Werttyp deklariert einen expliziten statischen Konstruktor. Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor.|
|[CA2208: Argumentausnahmen korrekt instanziieren.](../code-quality/ca2208.md)|Der (parameterlose) Standardkonstruktor eines Ausnahmetyps wird aufgerufen, der ArgumentException ist oder davon abgeleitet wird, oder ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps übergeben, der ArgumentException ist oder davon abgeleitet wird.|
|[CA2211: Nicht konstante Felder sollten nicht sichtbar sein.](../code-quality/ca2211.md)|Statische Felder, die keine Konstanten sind oder schreibgeschützt sind, sind nicht Thread sicher. Der Zugriff auf ein solches Feld muss sorgfältig gesteuert werden und erfordert erweiterte Programmierverfahren für die Synchronisierung des Zugriffs auf das Klassenobjekt.|
|[CA2213: Verwerfbare Felder verwerfen.](../code-quality/ca2213.md)|Ein Typ, der System.IDisposable implementiert, deklariert Felder von Typen, die ebenfalls IDisposable implementieren. Die Dispose-Methode des Felds wird nicht von der Dispose-Methode des deklarierenden Typs aufgerufen.|
|[CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen.](../code-quality/ca2214.md)|Wenn ein Konstruktor eine virtuelle Methode aufruft, ist es möglich, dass der Konstruktor für die-Instanz, die die-Methode aufruft, nicht ausgeführt wurde.|
|[CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen.](../code-quality/ca2215.md)|Wenn ein Typ von einem Typ erbt, der verworfen werden kann, muss von seiner Dispose-Methode die Dispose-Methode des Basistyps aufgerufen werden.|
|[CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren.](../code-quality/ca2216.md)|Ein Typ, der System. iverwerfimplementiert und über Felder verfügt, die die Verwendung nicht verwalteter Ressourcen vorschlagen, implementiert keinen Finalizer, wie von Object. Finalize beschrieben.|
|[CA2217: Enumerationen nicht mit FlagsAttribute markieren.](../code-quality/ca2217.md)|Eine extern sichtbare Enumeration wird mit FlagsAttribute gekennzeichnet und verfügt über einen oder mehrere Werte, die nicht aus zwei oder einer Kombination der anderen definierten Werte für die Enumeration bestehen.|
|[CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen.](../code-quality/ca2219.md)|Wenn eine Ausnahme in einer finally-Klausel oder fault-Klausel ausgelöst wird, wird die aktive Ausnahme von der neuen Ausnahme verdeckt. Wenn eine Ausnahme in einer filter-Klausel ausgelöst wird, fängt die Laufzeit die Ausnahme automatisch ab. Dadurch wird der ursprüngliche Fehler schwer zu erkennen und zu debuggen.|
|[CA2225: Operatorüberladungen weisen benannte Alternativen auf.](../code-quality/ca2225.md)|Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden. Der benannte Alternative Member bietet Zugriff auf die gleiche Funktionalität wie der-Operator und wird für Entwickler bereitgestellt, die in Sprachen programmieren, die überladene Operatoren nicht unterstützen.|
|[CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226.md)|Ein Typ implementiert den Gleichheits-oder Ungleichheits Operator und implementiert nicht den umgekehrten Operator.|
|[CA2227: Sammlungseigenschaften sollten schreibgeschützt sein.](../code-quality/ca2227.md)|Eine schreibbare Auflistungseigenschaft ermöglicht es Benutzern, die Auflistung durch eine andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu.|
|[CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229.md)|Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor.|
|[CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.](../code-quality/ca2231.md)|Ein Werttyp überschreibt, `Object.Equals` aber implementiert den Gleichheits Operator nicht.|
|[CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren.](../code-quality/ca2232.md)|STAThreadAttribute gibt an, dass das COM-Threadingmodell für die Anwendung ein Singlethread-Apartment ist. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig.|
|[CA2233: Vorgänge sollten nicht überlaufen.](../code-quality/ca2233.md)|Arithmetische Operationen sollten nicht ausgeführt werden, ohne zuerst die Operanden zu überprüfen, um sicherzustellen, dass das Ergebnis des Vorgangs nicht außerhalb des Bereichs möglicher Werte für die betroffenen Datentypen liegt.|
|[CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.](../code-quality/ca2234.md)|Eine Methode wird aufgerufen, die über einen Zeichenfolgenparameter verfügt, dessen Name "uri", "URI", "urn", "URN", "url" oder "URL" enthält.  Der deklarierende Typ der Methode enthält eine entsprechende Methodenüberladung, die über einen System.Uri-Parameter verfügt.|
|[CA2235: Alle nicht serialisierbaren Felder markieren.](../code-quality/ca2235.md)|Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert.|
|[CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.](../code-quality/ca2236.md)|Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die GetObjectData-Methode oder den Serialisierungskonstruktor des Basistyps in der Methode oder im Konstruktor des entsprechenden abgeleiteten Typs auf.|
|[CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237.md)|Um vom Common Language Runtime als serialisierbar erkannt zu werden, müssen Typen mit dem SerializableAttribute-Attribut markiert werden, auch wenn der Typ durch die Implementierung der iserialisierbaren Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet.|
|[CA2238: Serialisierungsmethoden korrekt implementieren.](../code-quality/ca2238.md)|Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit.|
|[CA2239: Deserialisierungsmethoden für optionale Felder angeben.](../code-quality/ca2239.md)|Ein Typ verfügt über ein Feld, das mit dem System. Runtime. Serialization. OptionalFieldAttribute-Attribut markiert ist, und der Typ stellt keine deserialisierungsereignisbehandlungsmethoden bereit.|
|[CA2240: ISerializable ordnungsgemäß implementieren.](../code-quality/ca2240.md)|Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die GetObjectData-Methode sichtbar und über schreibbar, und stellen Sie sicher, dass alle Instanzfelder in den Serialisierungsprozess eingeschlossen oder explizit mit dem NonSerializedAttribute-Attribut gekennzeichnet sind.|
|[CA2241: Geben Sie die korrekte Anzahl für Formatierungsmethoden an.](../code-quality/ca2241.md)|Das an System. String. Format über gegebene Format-Argument enthält kein Format Element, das jedem Objekt Argument entspricht, oder umgekehrt.|
|[CA2242: Ordnungsgemäß auf NaN testen.](../code-quality/ca2242.md)|Mit diesem Ausdruck testen Sie einen Wert auf Single.Nan oder Double.Nan. Testen Sie den Wert mithilfe von Single.IsNan(Single) oder Double.IsNan(Double).|
|[CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.](../code-quality/ca2243.md)|Der zeichenfolgenliteralparameter eines Attributs wird für eine URL, eine GUID oder eine Version nicht ordnungsgemäß analysiert.|
|[CA2244: Keine Initialisierungen indizierter Elemente duplizieren](../code-quality/ca2244.md)|Ein Objektinitialisierer verfügt über mehr als einen indizierten Elementinitialisierer mit demselben Konstanten Index. Alle außer der letzte Initialisierer sind redundant.|
|[CA2245: Keine Zuweisung einer Eigenschaft zu sich selbst](../code-quality/ca2245.md)|Eine Eigenschaft wurde versehentlich selbst zugewiesen.|
|[CA2246: Keine Zuweisung eines Symbols und seines Members in der gleichen Anweisung](../code-quality/ca2246.md)|Es wird nicht empfohlen, ein Symbol und dessen Member, d. h. ein Feld oder eine Eigenschaft, in derselben Anweisung zuzuweisen. Es ist nicht klar, ob der Element Zugriff dazu gedacht war, den alten Wert des Symbols vor der Zuweisung oder den neuen Wert aus der Zuweisung in dieser Anweisung zu verwenden.|
|[CA2247: Anstelle einer TaskContinuationOptions-Enumeration muss eine TaskCreationOptions-Enumeration als Argument an den TaskCompletionSource-Konstruktor übergeben werden.](../code-quality/ca2246.md)|TaskCompletionSource verfügt über Konstruktoren, die taskkreationoptions verwenden, die die zugrunde liegende Aufgabe steuern, und Konstruktoren, die den Objektzustand annehmen, der in der Aufgabe gespeichert ist.  Das versehentliche übergeben von TaskContinuationOptions anstelle von taskkreationoptions führt dazu, dass der Aufruf die Optionen als Zustand behandelt.|
|[CA2248: Geben Sie ein korrektes "Aufzählungs Argument" für "" "" "" ".](../code-quality/ca2248.md)|Der als Argument an den `HasFlag` Methodenaufruf umgegebene Aufzählungs Typ unterscheidet sich vom aufrufenden Aufzählungs Typen.|
|[CA2249: Erwägen Sie die Verwendung von "String.Contains" anstelle von "String.IndexOf"](../code-quality/ca2249.md)|Aufrufe `string.IndexOf` von, bei denen das Ergebnis verwendet wird, um zu überprüfen, ob eine Teil Zeichenfolge vorhanden oder nicht vorhanden ist, können durch ersetzt werden `string.Contains` .|

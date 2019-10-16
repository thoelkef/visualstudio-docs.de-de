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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f58701cbebb4b738b635fac0c2805f07b4a5266f
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349547"
---
# <a name="usage-warnings"></a>Verwendungswarnungen

Verwendungs Warnungen unterstützen die ordnungsgemäße Verwendung von .net.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801.md)|Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird.|
|[CA1806: Methodenergebnisse nicht ignorieren](../code-quality/ca1806.md)|Ein neues Objekt wird erstellt, aber nie verwendet, oder eine Methode wird aufgerufen, die eine neue Zeichenfolge erstellt und zurückgibt, die nie verwendet wird, oder eine COM-Methode oder P/Invoke-Methode gibt ein HRESULT oder einen Fehlercode zurück, das oder der nie verwendet wird.|
|[CA1816: GC.SuppressFinalize korrekt aufrufen](../code-quality/ca1816.md)|Eine Methode, bei der es sich um eine-Implementierung handelt, ruft keine GC auf. SuppressFinalize oder eine Methode, die keine Implementierung von verwerfen ist, ruft GC auf. SuppressFinalize oder eine Methode ruft GC auf. SuppressFinalize und übergibt etwas anderes als dieses (mich in Visual Basic).|
|[CA2200: Erneut ausführen, um Stapeldetails beizubehalten](../code-quality/ca2200.md)|Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird in der throw-Anweisung explizit angegeben. Wenn eine Ausnahme durch Angeben der Ausnahme in der throw-Anweisung erneut ausgelöst wird, geht die Liste der Methoden, die zwischen der Methode, durch die die Ausnahme ursprünglich ausgelöst wurde, und der aktuellen Methode aufgerufen wurden, verloren.|
|[CA2201: Keine reservierten Ausnahmetypen auslösen](../code-quality/ca2201.md)|Dadurch wird der ursprüngliche Fehler schwer zu erkennen und zu debuggen.|
|[CA2202: Objekte nicht mehrmals verwerfen](../code-quality/ca2202.md)|Eine Methodenimplementierung enthält Codepfade, die für dasselbe Objekt mehrere Aufrufe von System.IDisposable.Dispose oder einer Entsprechung von Dispose (z. B. einer Close()-Methode für bestimmte Typen) verursachen können.|
|[CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204.md)|Ein Zeichenfolgenliteral in einem Methodentext enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.|
|[CA2205: Verwaltete Entsprechungen der Win32-API verwenden](../code-quality/ca2205.md)|Eine Platt Form Aufruf Methode ist definiert, und eine .NET-Methode mit der entsprechenden Funktionalität ist verfügbar.|
|[CA2207: Statische Felder für Werttyp inline initialisieren](../code-quality/ca2207.md)|Ein Werttyp deklariert einen expliziten statischen Konstruktor. Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor.|
|[CA2208: Argumentausnahmen korrekt instanziieren](../code-quality/ca2208.md)|Der (parameterlose) Standardkonstruktor eines Ausnahmetyps wird aufgerufen, der ArgumentException ist oder davon abgeleitet wird, oder ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps übergeben, der ArgumentException ist oder davon abgeleitet wird.|
|[CA2211: Nicht konstante Felder sollten nicht sichtbar sein](../code-quality/ca2211.md)|Statische Felder, die keine Konstanten sind oder schreibgeschützt sind, sind nicht Thread sicher. Der Zugriff auf ein solches Feld muss sorgfältig gesteuert werden und erfordert erweiterte Programmierverfahren für die Synchronisierung des Zugriffs auf das Klassenobjekt.|
|[CA2212: ServicedComponents nicht mit WebMethod markieren](../code-quality/ca2212.md)|Eine Methode in einem Typ, der von System. EnterpriseServices. ServicedComponent erbt, ist mit System. Web. Services. WebMethodAttribute markiert. Da das Verhalten von WebMethodAttribute und einer ServicedComponent-Methode sowie deren Anforderungen an den Kontext sowie den Transaktionsablauf zu Konflikten führen, ist das Verhalten der Methode in bestimmten Szenarien fehlerhaft.|
|[CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213.md)|Ein Typ, der System.IDisposable implementiert, deklariert Felder von Typen, die ebenfalls IDisposable implementieren. Die Dispose-Methode des Felds wird nicht von der Dispose-Methode des deklarierenden Typs aufgerufen.|
|[CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen](../code-quality/ca2214.md)|Wenn ein Konstruktor eine virtuelle Methode aufruft, ist es möglich, dass der Konstruktor für die-Instanz, die die-Methode aufruft, nicht ausgeführt wurde.|
|[CA2215: Dispose-Methoden müssen die Dispose-Funktion der Basisklasse aufrufen](../code-quality/ca2215.md)|Wenn ein Typ von einem Typ erbt, der verworfen werden kann, muss von seiner Dispose-Methode die Dispose-Methode des Basistyps aufgerufen werden.|
|[CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216.md)|Ein Typ, der System. iverwerfimplementiert und über Felder verfügt, die die Verwendung nicht verwalteter Ressourcen vorschlagen, implementiert keinen Finalizer, wie von Object. Finalize beschrieben.|
|[CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217.md)|Eine extern sichtbare Enumeration wird mit FlagsAttribute gekennzeichnet und verfügt über einen oder mehrere Werte, die nicht aus zwei oder einer Kombination der anderen definierten Werte für die Enumeration bestehen.|
|[CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218.md)|GetHashCode gibt einen Wert auf der Grundlage der aktuellen Instanz zurück, die sich für Hashalgorithmen und Datenstrukturen eignet, z. B. für eine Hashtabelle. Zwei Objekte, die denselben Typ aufweisen und gleich sind, müssen den gleichen Hashcode zurückgeben.|
|[CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen](../code-quality/ca2219.md)|Wenn eine Ausnahme in einer finally-Klausel oder fault-Klausel ausgelöst wird, wird die aktive Ausnahme von der neuen Ausnahme verdeckt. Wenn eine Ausnahme in einer filter-Klausel ausgelöst wird, fängt die Laufzeit die Ausnahme automatisch ab. Dadurch wird der ursprüngliche Fehler schwer zu erkennen und zu debuggen.|
|[CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen](../code-quality/ca2220.md)|Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies zu garantieren, müssen die Typen die Finalize-Methode ihrer Basisklasse in der eigenen Finalize-Methode aufrufen.|
|[CA2221: Finalizer sollten geschützt sein](../code-quality/ca2221.md)|Finalizer müssen den Familienzugriffsmodifizierer verwenden.|
|[CA2222: Sichtbarkeit für geerbte Member nicht verringern](../code-quality/ca2222.md)|Ändern Sie den Zugriffsmodifizierer für geerbte Member nicht Wenn Sie einen geerbten Member in private ändern, werden Aufrufer nicht am Zugriff auf die Implementierung der Basisklasse der Methode gehindert.|
|[CA2223: Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden](../code-quality/ca2223.md)|Die Common Language Runtime lässt die Verwendung von Rückgabetypen zu, mit deren Hilfe zwischen anderweitig identischen Membern unterschieden werden kann. Trotzdem ist diese Funktion nicht in der Common Language Specification (CLS) enthalten und keine gebräuchliche Funktion von .NET-Programmiersprachen.|
|[CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224.md)|Ein öffentlicher Typ implementiert den Gleichheits Operator, überschreibt jedoch nicht Object. ist gleich.|
|[CA2225: Operatorüberladungen weisen benannte Alternativen auf](../code-quality/ca2225.md)|Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden. Der benannte Alternative Member bietet Zugriff auf die gleiche Funktionalität wie der-Operator und wird für Entwickler bereitgestellt, die in Sprachen programmieren, die überladene Operatoren nicht unterstützen.|
|[CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226.md)|Ein Typ implementiert den Gleichheits-oder Ungleichheits Operator und implementiert nicht den umgekehrten Operator.|
|[CA2227: Auflistungseigenschaften sollten schreibgeschützt sein](../code-quality/ca2227.md)|Eine schreibbare Auflistungseigenschaft ermöglicht es Benutzern, die Auflistung durch eine andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu.|
|[CA2228: Nicht freigegebene Ressourcenformate nicht veröffentlichen](../code-quality/ca2228.md)|Ressourcen Dateien, die mithilfe von vorab Versionen von .NET erstellt wurden, können möglicherweise nicht von unterstützten Versionen von .NET verwendet werden.|
|[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229.md)|Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor.|
|[CA2230: params für Variablenargumente verwenden](../code-quality/ca2230.md)|Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, die statt des params-Schlüsselworts die VarArgs-Aufrufkonvention verwendet.|
|[CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231.md)|Ein Werttyp überschreibt `Object.Equals`, implementiert aber nicht den Gleichheits Operator.|
|[CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren](../code-quality/ca2232.md)|STAThreadAttribute gibt an, dass das COM-Threadingmodell für die Anwendung ein Singlethread-Apartment ist. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig.|
|[CA2233: Vorgänge sollten nicht überlaufen](../code-quality/ca2233.md)|Arithmetische Operationen sollten nicht ausgeführt werden, ohne zuerst die Operanden zu überprüfen, um sicherzustellen, dass das Ergebnis des Vorgangs nicht außerhalb des Bereichs möglicher Werte für die betroffenen Datentypen liegt.|
|[CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234.md)|Eine Methode wird aufgerufen, die über einen Zeichenfolgenparameter verfügt, dessen Name "uri", "URI", "urn", "URN", "url" oder "URL" enthält.  Der deklarierende Typ der Methode enthält eine entsprechende Methodenüberladung, die über einen System.Uri-Parameter verfügt.|
|[CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235.md)|Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert.|
|[CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen](../code-quality/ca2236.md)|Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die GetObjectData-Methode oder den Serialisierungskonstruktor des Basistyps in der Methode oder im Konstruktor des entsprechenden abgeleiteten Typs auf.|
|[CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237.md)|Um vom Common Language Runtime als serialisierbar erkannt zu werden, müssen Typen mit dem SerializableAttribute-Attribut markiert werden, auch wenn der Typ durch die Implementierung der iserialisierbaren Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet.|
|[CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238.md)|Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit.|
|[CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239.md)|Ein Typ verfügt über ein Feld, das mit dem System. Runtime. Serialization. OptionalFieldAttribute-Attribut markiert ist, und der Typ stellt keine deserialisierungsereignisbehandlungsmethoden bereit.|
|[CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240.md)|Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die GetObjectData-Methode sichtbar und über schreibbar, und stellen Sie sicher, dass alle Instanzfelder in den Serialisierungsprozess eingeschlossen oder explizit mit dem NonSerializedAttribute-Attribut gekennzeichnet sind.|
|[CA2241: Geeignete Argumente für Formatierungsmethoden angeben](../code-quality/ca2241.md)|Das an System. String. Format über gegebene Format-Argument enthält kein Format Element, das jedem Objekt Argument entspricht, oder umgekehrt.|
|[CA2242: Ordnungsgemäß auf NaN testen](../code-quality/ca2242.md)|Mit diesem Ausdruck testen Sie einen Wert auf Single.Nan oder Double.Nan. Testen Sie den Wert mithilfe von Single.IsNan(Single) oder Double.IsNan(Double).|
|[CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden](../code-quality/ca2243.md)|Der zeichenfolgenliteralparameter eines Attributs wird für eine URL, eine GUID oder eine Version nicht ordnungsgemäß analysiert.|

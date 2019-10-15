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
ms.openlocfilehash: e607da01d160212eea03b1fe81dfb2fbf4ede3f6
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305685"
---
# <a name="usage-warnings"></a>Verwendungswarnungen

Verwendungs Warnungen unterstützen die ordnungsgemäße Verwendung von .net.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1801: Nicht verwendete Parameter überprüfen @ no__t-0|Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird.|
|[CA1806: Methoden Ergebnisse nicht ignorieren @ no__t-0|Ein neues Objekt wird erstellt, aber nie verwendet, oder eine Methode wird aufgerufen, die eine neue Zeichenfolge erstellt und zurückgibt, die nie verwendet wird, oder eine COM-Methode oder P/Invoke-Methode gibt ein HRESULT oder einen Fehlercode zurück, das oder der nie verwendet wird.|
|[CA1816: Ruft GC auf. SuppressFinalize ordnungsgemäß @ no__t-0|Eine Methode, die eine Implementierung von Dispose bildet, ruft nicht GC auf. SuppressFinalize; oder eine Methode, die eine Implementierung von Dispose nicht ist, ruft GC. SuppressFinalize; oder eine Methode aufruft, GC. SuppressFinalize aus und übergibt ein anderes Element als dieses (Me in Visual Basic).|
|[CA2200: Zum Beibehalten der Stapel Details erneut auslösen @ no__t-0|Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird in der throw-Anweisung explizit angegeben. Wenn eine Ausnahme durch Angeben der Ausnahme in der throw-Anweisung erneut ausgelöst wird, geht die Liste der Methoden, die zwischen der Methode, durch die die Ausnahme ursprünglich ausgelöst wurde, und der aktuellen Methode aufgerufen wurden, verloren.|
|[CA2201: Keine reservierten Ausnahme Typen no__t-0|Dadurch wird der ursprüngliche Fehler schwer zu erkennen und zu debuggen.|
|[CA2202: Objekte nicht mehrmals löschen @ no__t-0|Eine Methodenimplementierung enthält Codepfade, die für dasselbe Objekt mehrere Aufrufe von System.IDisposable.Dispose oder einer Entsprechung von Dispose (z. B. einer Close()-Methode für bestimmte Typen) verursachen können.|
|[CA2204: Literale müssen ordnungsgemäß geschrieben werden @ no__t-0|Ein Zeichenfolgenliteral in einem Methodentext enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.|
|[CA2205: Verwaltete Entsprechungen der Win32-API @ no__t-0 verwenden|Eine Platt Form Aufruf Methode ist definiert, und eine .NET-Methode mit der entsprechenden Funktionalität ist verfügbar.|
|[CA2207: Statische Felder für Werttyp initialisieren Inline @ no__t-0|Ein Werttyp deklariert einen expliziten statischen Konstruktor. Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor.|
|[CA2208: Argument Ausnahmen ordnungsgemäß instanziieren @ no__t-0|Der (parameterlose) Standardkonstruktor eines Ausnahmetyps wird aufgerufen, der ArgumentException ist oder davon abgeleitet wird, oder ein falsches Zeichenfolgenargument wird an einen parametrisierten Konstruktor eines Ausnahmetyps übergeben, der ArgumentException ist oder davon abgeleitet wird.|
|[CA2211: Nicht konstante Felder dürfen nicht sichtbar sein @ no__t-0|Statische Felder, die keine Konstanten sind oder schreibgeschützt sind, sind nicht Thread sicher. Der Zugriff auf ein solches Feld muss sorgfältig gesteuert werden und erfordert erweiterte Programmierverfahren für die Synchronisierung des Zugriffs auf das Klassenobjekt.|
|[CA2212: Verwenden Sie keine Serviced Components mit WebMethod @ no__t-0|Eine Methode in einem Typ, der von System. EnterpriseServices. ServicedComponent erbt, ist mit System. Web. Services. WebMethodAttribute markiert. Da das Verhalten von WebMethodAttribute und einer ServicedComponent-Methode sowie deren Anforderungen an den Kontext sowie den Transaktionsablauf zu Konflikten führen, ist das Verhalten der Methode in bestimmten Szenarien fehlerhaft.|
|[CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Ein Typ, der System.IDisposable implementiert, deklariert Felder von Typen, die ebenfalls IDisposable implementieren. Die Dispose-Methode des Felds wird nicht von der Dispose-Methode des deklarierenden Typs aufgerufen.|
|[CA2214: Über schreibbare Methoden in Konstruktoren nicht aufzurufen @ no__t-0|Wenn ein Konstruktor eine virtuelle Methode aufruft, ist es möglich, dass der Konstruktor für die-Instanz, die die-Methode aufruft, nicht ausgeführt wurde.|
|[CA2215: Verwerfen-Methoden sollten Basisklasse verwerfen @ no__t-0|Wenn ein Typ von einem Typ erbt, der verworfen werden kann, muss von seiner Dispose-Methode die Dispose-Methode des Basistyps aufgerufen werden.|
|[CA2216: Verwerfbare Typen sollten den Finalizer @ no__t-0 deklarieren.|Ein Typ, der System. iverwerfimplementiert und über Felder verfügt, die die Verwendung nicht verwalteter Ressourcen vorschlagen, implementiert keinen Finalizer, wie von Object. Finalize beschrieben.|
|[CA2217: Markieren Sie die auffüge Zeichen nicht mit FlagsAttribute @ no__t-0.|Eine extern sichtbare Enumeration wird mit FlagsAttribute gekennzeichnet und verfügt über einen oder mehrere Werte, die nicht aus zwei oder einer Kombination der anderen definierten Werte für die Enumeration bestehen.|
|[CA2218: GetHashCode beim Überschreiben von Gleichheits @ no__t-0 überschreiben|GetHashCode gibt einen Wert auf der Grundlage der aktuellen Instanz zurück, die sich für Hashalgorithmen und Datenstrukturen eignet, z. B. für eine Hashtabelle. Zwei Objekte, die denselben Typ aufweisen und gleich sind, müssen den gleichen Hashcode zurückgeben.|
|[CA2219: Keine Ausnahmen in Ausnahmeklauseln (@ no__t-0)|Wenn eine Ausnahme in einer finally-Klausel oder fault-Klausel ausgelöst wird, wird die aktive Ausnahme von der neuen Ausnahme verdeckt. Wenn eine Ausnahme in einer filter-Klausel ausgelöst wird, fängt die Laufzeit die Ausnahme automatisch ab. Dadurch wird der ursprüngliche Fehler schwer zu erkennen und zu debuggen.|
|[CA2220: Finalizer sollten den Basisklassen-Finalizer @ no__t-0 abrufen.|Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies zu garantieren, müssen die Typen die Finalize-Methode ihrer Basisklasse in der eigenen Finalize-Methode aufrufen.|
|[CA2221: Finalizer sollten geschützt sein @ no__t-0|Finalizer müssen den Familienzugriffsmodifizierer verwenden.|
|[CA2222: Sichtbarkeit für geerbte Member nicht verringern @ no__t-0|Ändern Sie den Zugriffsmodifizierer für geerbte Member nicht Wenn Sie einen geerbten Member in private ändern, werden Aufrufer nicht am Zugriff auf die Implementierung der Basisklasse der Methode gehindert.|
|[CA2223: Member sollten sich um mehr als den Rückgabetyp @ no__t-0 unterscheiden.|Die Common Language Runtime lässt die Verwendung von Rückgabetypen zu, mit deren Hilfe zwischen anderweitig identischen Membern unterschieden werden kann. Trotzdem ist diese Funktion nicht in der Common Language Specification (CLS) enthalten und keine gebräuchliche Funktion von .NET-Programmiersprachen.|
|[CA2224: Außerkraftsetzungs Wert beim Überladen des Operators ist "@ no__t-0"|Ein öffentlicher Typ implementiert den Gleichheits Operator, überschreibt jedoch nicht Object. ist gleich.|
|[CA2225: Operator Überladungen haben benannte Alternativen @ no__t-0|Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden. Der benannte Alternative Member bietet Zugriff auf die gleiche Funktionalität wie der-Operator und wird für Entwickler bereitgestellt, die in Sprachen programmieren, die überladene Operatoren nicht unterstützen.|
|[CA2226: Operatoren sollten symmetrische über Ladungen aufweisen @ no__t-0|Ein Typ implementiert den Gleichheits-oder Ungleichheits Operator und implementiert nicht den umgekehrten Operator.|
|[CA2227: Sammlungs Eigenschaften sollten schreibgeschützt sein @ no__t-0|Eine schreibbare Auflistungseigenschaft ermöglicht es Benutzern, die Auflistung durch eine andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu.|
|[CA2228: Nicht freigegebene Ressourcen Formate nicht senden @ no__t-0|Ressourcen Dateien, die mithilfe von vorab Versionen von .NET erstellt wurden, können möglicherweise nicht von unterstützten Versionen von .NET verwendet werden.|
|[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)|Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor.|
|[CA2230: Params für Variablen Argumente verwenden @ no__t-0|Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, die statt des params-Schlüsselworts die VarArgs-Aufrufkonvention verwendet.|
|[CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Ein Werttyp überschreibt `Object.Equals`, implementiert aber nicht den Gleichheits Operator.|
|[CA2232: Markieren Sie Windows Forms Einstiegspunkte mit STAThread @ no__t-0|STAThreadAttribute gibt an, dass das COM-Threadingmodell für die Anwendung ein Singlethread-Apartment ist. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig.|
|[CA2233: Vorgänge sollten nicht Überlauf @ no__t-0|Arithmetische Operationen sollten nicht ausgeführt werden, ohne zuerst die Operanden zu überprüfen, um sicherzustellen, dass das Ergebnis des Vorgangs nicht außerhalb des Bereichs möglicher Werte für die betroffenen Datentypen liegt.|
|[CA2234: Übergeben Sie System. URI-Objekte anstelle von Zeichen folgen @ no__t-0|Eine Methode wird aufgerufen, die über einen Zeichenfolgenparameter verfügt, dessen Name "uri", "URI", "urn", "URN", "url" oder "URL" enthält.  Der deklarierende Typ der Methode enthält eine entsprechende Methodenüberladung, die über einen System.Uri-Parameter verfügt.|
|[CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert.|
|[CA2236: Abrufen von Basisklassen Methoden für iserialisierbare Typen @ no__t-0|Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die GetObjectData-Methode oder den Serialisierungskonstruktor des Basistyps in der Methode oder im Konstruktor des entsprechenden abgeleiteten Typs auf.|
|[CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute @ no__t-0|Um vom Common Language Runtime als serialisierbar erkannt zu werden, müssen Typen mit dem SerializableAttribute-Attribut markiert werden, auch wenn der Typ durch die Implementierung der iserialisierbaren Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet.|
|[CA2238: Implementieren Sie Serialisierungsmethoden ordnungsgemäß @ no__t-0|Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit.|
|[CA2239: Stellen Sie Deserialisierungsmethoden für optionale Felder @ no__t-0 bereit.|Ein Typ verfügt über ein Feld, das mit dem System. Runtime. Serialization. OptionalFieldAttribute-Attribut markiert ist, und der Typ stellt keine deserialisierungsereignisbehandlungsmethoden bereit.|
|[CA2240: Implementieren Sie iserialisierbar ordnungsgemäß @ no__t-0|Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die GetObjectData-Methode sichtbar und über schreibbar, und stellen Sie sicher, dass alle Instanzfelder in den Serialisierungsprozess eingeschlossen oder explizit mit dem NonSerializedAttribute-Attribut gekennzeichnet sind.|
|[CA2241: Angeben korrekter Argumente für Formatierungs Methoden @ no__t-0|Das an System. String. Format über gegebene Format-Argument enthält kein Format Element, das jedem Objekt Argument entspricht, oder umgekehrt.|
|[CA2242: Ordnungsgemäße Tests für Nan @ no__t-0|Mit diesem Ausdruck testen Sie einen Wert auf Single.Nan oder Double.Nan. Testen Sie den Wert mithilfe von Single.IsNan(Single) oder Double.IsNan(Double).|
|[CA2243: Attribut Zeichenfolgenliterale müssen ordnungsgemäß analysiert werden @ no__t-0|Der zeichenfolgenliteralparameter eines Attributs wird für eine URL, eine GUID oder eine Version nicht ordnungsgemäß analysiert.|
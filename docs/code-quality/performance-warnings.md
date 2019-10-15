---
title: Leistungswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29ace36d35b31eeb3635d06d6244ac6fe0897ec2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305660"
---
# <a name="performance-warnings"></a>Leistungswarnungen
Leistungs Warnungen unterstützen Hochleistungs Bibliotheken und-Anwendungen.

## <a name="in-this-section"></a>In diesem Abschnitt

| Regel | Beschreibung |
| - | - |
| [CA1800: Unnötigerweise nicht umwandeln (@ no__t-0) | Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. |
| [CA1801: Nicht verwendete Parameter überprüfen @ no__t-0 | Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. |
| [CA1802: Verwenden Sie Literale, sofern zutreffend @ no__t-0 | Ein Feld wird als statisch und schreibgeschützt deklariert (freigegeben und schreibgeschützt in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) und mit einem Wert initialisiert, der zur Kompilierzeit berechnet werden kann. Da der Wert, der dem verwendeten Feld zugewiesen wird zum Zeitpunkt der Kompilierung zu berechnendes ist, ändern Sie die Deklaration in ein Const (Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Feld, sodass der Wert zur Kompilierzeit statt zur Laufzeit berechnet wird. |
| [CA1804: Nicht verwendete lokale Variablen entfernen @ no__t-0 | Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung. |
| [CA1806: Methoden Ergebnisse nicht ignorieren @ no__t-0 | Ein neues-Objekt wird erstellt, aber nie verwendet, oder eine Methode, die eine neue Zeichenfolge erstellt und zurückgibt, wird aufgerufen, und die neue Zeichenfolge wird nie verwendet, oder eine Component Object Model (com)-oder P/aufrufen-Methode gibt ein HRESULT oder einen Fehlercode zurück, das nie verwendet wird. |
| [CA1809: Übermäßige lokale Variablen vermeiden @ no__t-0 | Zur Leistungsoptimierung wird ein Wert häufig in einem Prozessorregister statt im Speicher gespeichert. Dieser Vorgang wird als Registrierung des Werts bezeichnet.  Um die Wahrscheinlichkeit zu erhöhen, dass alle lokale Variablen registriert werden, die Anzahl der lokalen Variablen auf 64. |
| [CA1810: Statische Felder für Verweistyp initialisieren Inline @ no__t-0 | Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT-Compiler (Just in Time) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde. Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden. |
| [CA1811: Nicht aufgerufenen privaten Code vermeiden @ no__t-0 | Ein privater oder interner Member (auf Assemblyebene) verfügt nicht über Aufrufer in der Assembly, er wird nicht vom Common Language Runtime aufgerufen und wird nicht von einem Delegaten aufgerufen. |
| [CA1812: Nicht instanziierte interne Klassen vermeiden @ no__t-0 | Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt. |
| [CA1813: Nicht versiegelte Attribute vermeiden @ no__t-0 | .NET stellt Methoden zum Abrufen von benutzerdefinierten Attributen bereit. Standardmäßig wird mit diesen Methoden die Attributvererbungshierarchie durchsucht. Durch Verwendung eines versiegelten Attributs wird das Durchsuchen der Vererbungshierarchie unterbunden und die Leistung u. U. verbessert. |
| [CA1814: Verzweigte Arrays vor mehr dimensionalem @ no__t-0 bevorzugen | Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind. Die Arrays, aus denen die Elemente bestehen, können unterschiedlich groß sein, was zu weniger Verlust von Speicherplatz für einige Datenmengen führen kann. |
| [CA1815: Override equals and operator equals on value types (CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben)](../code-quality/ca1815.md). | Bei Werttypen wird die Reflection-Bibliothek von der geerbten Implementierung von Equals verwendet und der Inhalt aller Felder verglichen. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren bzw. dass sie die Instanzen als Schlüssel für Hashtabellen verwenden, sollte der Werttyp Equals implementieren. |
| [CA1816: Ruft GC auf. SuppressFinalize ordnungsgemäß @ no__t-0 | Eine Methode, bei der es sich um eine-Implementierung handelt, ruft keine GC auf. SuppressFinalize oder eine Methode, die keine Implementierung von verwerfen ist, ruft GC auf. SuppressFinalize oder eine Methode ruft GC auf. SuppressFinalize und übergibt etwas anderes als dieses (mich in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Eigenschaften sollten keine Arrays zurückgeben @ no__t-0 | Arrays, die von Eigenschaften zurückgegeben werden, sind nicht schreibgeschützt, auch wenn die Eigenschaft schreibgeschützt ist. Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben. Normalerweise verstehen die Benutzer nicht, welche negativen Auswirkungen der Aufruf einer solchen Eigenschaft auf die Leistung hat. |
| [CA1820: Testen von leeren Zeichen folgen mithilfe der Zeichen folgen Länge @ no__t-0 | Der Vergleich von Zeichenfolgen mit der String.Length-Eigenschaft oder der String.IsNullOrEmpty-Methode führt erheblich schneller zu Ergebnissen als das Verwenden von Equals. |
| [CA1821: Leere Finalizer entfernen](../code-quality/ca1821.md) | Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird. Ein leerer Finalizer verursacht zusätzlichen Aufwand ohne jeglichen Vorteil. |
| [CA1822: Member als statisch markieren @ no__t-0 | Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Dies kann zu einer messbaren Leistungssteigerung für leistungsabhängigen Code führen. |
| [CA1823: Nicht verwendete private Felder vermeiden @ no__t-0 | Es wurden private Felder erkannt, auf die in der Assembly anscheinend kein Zugriff erfolgt. |
| [CA1824: Assemblys mit NeutralResourcesLanguageAttribute @ no__t-0 markieren | Mit dem NeutralResourcesLanguage-Attribut wird dem ResourceManager die Sprache mitgeteilt, in der die Ressourcen einer neutralen Kultur für eine Assembly angezeigt wurden. Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern. |
| [CA1825: Array Belegungen der Länge 0 (null) vermeiden no__t-0 | Die Initialisierung eines Arrays der Länge 0 (null) führt zu einer unnötigen Speicher Belegung. Verwenden Sie stattdessen die statisch zugeordnete leere Array Instanz, indem Sie <xref:System.Array.Empty%2A?displayProperty=nameWithType> aufrufen. Die Speicher Belegung wird für alle Aufrufe dieser Methode freigegeben. |

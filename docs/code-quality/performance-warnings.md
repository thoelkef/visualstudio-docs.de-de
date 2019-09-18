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
ms.openlocfilehash: f8d8f06fe0d3d1e114662a8ea99d1458d65e3e4c
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079248"
---
# <a name="performance-warnings"></a>Leistungswarnungen
Leistungs Warnungen unterstützen Hochleistungs Bibliotheken und-Anwendungen.

## <a name="in-this-section"></a>In diesem Abschnitt

| Regel | Beschreibung |
| - | - |
| [CA1800: Nicht unnötig umwandeln](../code-quality/ca1800-do-not-cast-unnecessarily.md) | Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. |
| [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md) | Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. |
| [CA1802: Verwenden Sie nach Bedarf Literale.](../code-quality/ca1802-use-literals-where-appropriate.md) | Ein Feld wird als statisch und schreibgeschützt deklariert (Shared und Read only in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) und wird mit einem Wert initialisiert, der zur Kompilierzeit berechnet werden kann. Da der Wert, der dem verwendeten Feld zugewiesen wird zum Zeitpunkt der Kompilierung zu berechnendes ist, ändern Sie die Deklaration in ein Const (Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Feld, sodass der Wert zur Kompilierzeit statt zur Laufzeit berechnet wird. |
| [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md) | Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung. |
| [CA1806: Methoden Ergebnisse nicht ignorieren](../code-quality/ca1806-do-not-ignore-method-results.md) | Ein neues-Objekt wird erstellt, aber nie verwendet, oder eine Methode, die eine neue Zeichenfolge erstellt und zurückgibt, wird aufgerufen, und die neue Zeichenfolge wird nie verwendet, oder eine Component Object Model (com)-oder P/aufrufen-Methode gibt ein HRESULT oder einen Fehlercode zurück, das nie verwendet wird. |
| [CA1809: Übermäßige lokale Variablen vermeiden](../code-quality/ca1809-avoid-excessive-locals.md) | Zur Leistungsoptimierung wird ein Wert häufig in einem Prozessorregister statt im Speicher gespeichert. Dieser Vorgang wird als Registrierung des Werts bezeichnet.  Um die Wahrscheinlichkeit zu erhöhen, dass alle lokale Variablen registriert werden, die Anzahl der lokalen Variablen auf 64. |
| [CA1810: Statische Felder von Verweis Typen Inline initialisieren](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md) | Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT-Compiler (Just in Time) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde. Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden. |
| [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md) | Ein privater oder interner Member (auf Assemblyebene) verfügt nicht über Aufrufer in der Assembly, er wird nicht vom Common Language Runtime aufgerufen und wird nicht von einem Delegaten aufgerufen. |
| [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md) | Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt. |
| [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md) | .NET stellt Methoden zum Abrufen von benutzerdefinierten Attributen bereit. Standardmäßig wird mit diesen Methoden die Attributvererbungshierarchie durchsucht. Durch Verwendung eines versiegelten Attributs wird das Durchsuchen der Vererbungshierarchie unterbunden und die Leistung u. U. verbessert. |
| [CA1814: Verzweigte Arrays vor mehrdimensionalen Arrays bevorzugen](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md) | Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind. Die Arrays, aus denen die Elemente bestehen, können unterschiedlich groß sein, was zu weniger Verlust von Speicherplatz für einige Datenmengen führen kann. |
| [CA1815: Override equals and operator equals on value types (CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben)](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md). | Bei Werttypen wird die Reflection-Bibliothek von der geerbten Implementierung von Equals verwendet und der Inhalt aller Felder verglichen. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren bzw. dass sie die Instanzen als Schlüssel für Hashtabellen verwenden, sollte der Werttyp Equals implementieren. |
| [CA1816: Ruft GC auf. Ordnungsgemäße SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md) | Eine Methode, bei der es sich um eine-Implementierung handelt, ruft keine GC auf. SuppressFinalize oder eine Methode, die keine Implementierung von verwerfen ist, ruft GC auf. SuppressFinalize oder eine Methode ruft GC auf. SuppressFinalize und übergibt etwas anderes als dieses (ich in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md) | Arrays, die von Eigenschaften zurückgegeben werden, sind nicht schreibgeschützt, auch wenn die Eigenschaft schreibgeschützt ist. Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben. Normalerweise verstehen die Benutzer nicht, welche negativen Auswirkungen der Aufruf einer solchen Eigenschaft auf die Leistung hat. |
| [CA1820: Mithilfe der Zeichen folgen Länge auf leere Zeichen folgen prüfen](../code-quality/ca1820-test-for-empty-strings-using-string-length.md) | Der Vergleich von Zeichenfolgen mit der String.Length-Eigenschaft oder der String.IsNullOrEmpty-Methode führt erheblich schneller zu Ergebnissen als das Verwenden von Equals. |
| [CA1821: Leere Finalizer entfernen](../code-quality/ca1821-remove-empty-finalizers.md) | Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird. Ein leerer Finalizer verursacht zusätzlichen Aufwand ohne jeglichen Vorteil. |
| [CA1822: Member als statisch markieren](../code-quality/ca1822-mark-members-as-static.md) | Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Dies kann zu einer messbaren Leistungssteigerung für leistungsabhängigen Code führen. |
| [CA1823: Nicht verwendete private Felder vermeiden](../code-quality/ca1823-avoid-unused-private-fields.md) | Es wurden private Felder erkannt, auf die in der Assembly anscheinend kein Zugriff erfolgt. |
| [CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | Mit dem NeutralResourcesLanguage-Attribut wird dem ResourceManager die Sprache mitgeteilt, in der die Ressourcen einer neutralen Kultur für eine Assembly angezeigt wurden. Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern. |
| [CA1825: Array Belegungen mit einer Länge von NULL vermeiden](../code-quality/ca1825.md) | Die Initialisierung eines Arrays der Länge 0 (null) führt zu einer unnötigen Speicher Belegung. Verwenden Sie stattdessen die statisch zugeordnete leere Array Instanz, indem <xref:System.Array.Empty%2A?displayProperty=nameWithType>Sie aufrufen. Die Speicher Belegung wird für alle Aufrufe dieser Methode freigegeben. |

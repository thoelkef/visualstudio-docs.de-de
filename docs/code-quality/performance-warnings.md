---
title: "Leistungswarnungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.performancerules"
helpviewer_keywords: 
  - "Warnungen, Leistung"
  - "Leistungswarnungen"
  - "Leistung, Warnungen"
  - "Analysen für verwalteten Code (Warnungen), Leistungswarnungen"
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# Leistungswarnungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Leistungswarnungen unterstützen Hochleistungsbibliotheken und \-anwendungen.  
  
## In diesem Abschnitt  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[CA1800: Keine unnötigen Umwandlungen](../code-quality/ca1800-do-not-cast-unnecessarily.md)|Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden.|  
|[CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)|Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird.|  
|[CA1802: Nach Möglichkeit Literale verwenden](../code-quality/ca1802-use-literals-where-appropriate.md)|Ein Feld wird als static und read\-only deklariert \(Shared und ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) und mit einem Wert initialisiert, der zur Kompilierungszeit berechnet werden kann.  Da der dem verwendeten Feld zugewiesene Wert zur Kompilierungszeit berechnet werden kann, ändern Sie die Deklaration in ein const\-Feld \(Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), sodass der Wert statt zur Laufzeit zur Kompilierungszeit berechnet wird.|  
|[CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)|Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung.|  
|[CA1806: Methodenergebnisse nicht ignorieren](../code-quality/ca1806-do-not-ignore-method-results.md)|Ein neues Objekt wird erstellt, aber nie verwendet, oder eine Methode wird aufgerufen, die eine neue Zeichenfolge erstellt und zurückgibt, die nie verwendet wird, oder eine COM\-Methode \(Component Object Model\) oder P\/Invoke\-Methode gibt ein HRESULT oder einen Fehlercode zurück, das oder der nie verwendet wird.|  
|[CA1809: Übermäßige lokale Variablen vermeiden](../code-quality/ca1809-avoid-excessive-locals.md)|Zur Leistungsoptimierung wird ein Wert häufig in einem Prozessorregister statt im Speicher gespeichert. Dieser Vorgang wird als Registrierung des Werts bezeichnet.  Um die Wahrscheinlichkeit zu erhöhen, dass alle lokalen Variablen registriert werden, müssen Sie die Anzahl der lokalen Variablen auf 64 beschränken.|  
|[CA1810: Statische Felder von Verweistypen inline initialisieren](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT\-Compiler \(Just in Time\) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde.  Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden.|  
|[CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)|Zu einem privaten oder internen Member \(auf Assemblyebene\) gibt es in der Assembly keine Aufrufer, er wird nicht durch die Common Language Runtime und nicht durch einen Delegaten aufgerufen.|  
|[CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt.|  
|[CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)|Die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Klassenbibliothek stellt Methoden zum Abrufen benutzerdefinierter Attribute bereit.  Standardmäßig wird mit diesen Methoden die Attributvererbungshierarchie durchsucht.  Durch Verwendung eines versiegelten Attributs wird das Durchsuchen der Vererbungshierarchie unterbunden und die Leistung u. U. verbessert.|  
|[CA1814: Verzweigte Arrays mehrdimensionalen Arrays vorziehen](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind.  Die Arrays, die die Elemente bilden, können unterschiedliche Größen haben, was bei einigen Gruppen von Daten dazu führen kann, dass weniger Speicherplatz vergeudet wird.|  
|[CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Bei Werttypen wird die Reflection\-Bibliothek von der geerbten Implementierung von Equals verwendet und der Inhalt aller Felder verglichen.  Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig.  Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren bzw. dass sie die Instanzen als Schlüssel für Hashtabellen verwenden, sollte der Werttyp Equals implementieren.|  
|[CA1816: GC.SuppressFinalize korrekt aufrufen](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Eine Methode, die eine Implementierung von Dispose bildet, ruft nicht GC.SuppressFinalize auf, oder eine Methode, die keine Implementierung von Dispose bildet, ruft GC.SuppressFinalize auf, oder eine Methode ruft GC.SuppressFinalize auf und übergibt ein anderes Element als dieses \(Me in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).|  
|[CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md)|Von Eigenschaften zurückgegebene Arrays sind nicht schreibgeschützt, auch wenn die Eigenschaft schreibgeschützt ist.  Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben.  Normalerweise verstehen die Benutzer nicht, welche negativen Auswirkungen der Aufruf einer solchen Eigenschaft auf die Leistung hat.|  
|[CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Der Vergleich von Zeichenfolgen mit der String.Length\-Eigenschaft oder der String.IsNullOrEmpty\-Methode führt erheblich schneller zu Ergebnissen als das Verwenden von Equals.|  
|[CA1821: Leere Finalizer entfernen](../code-quality/ca1821-remove-empty-finalizers.md)|Finalizer sollten möglichst vermieden werden, da durch Verfolgung der Objektlebensdauer zusätzliche Leistung beansprucht wird.  Ein leerer Finalizer verursacht zusätzlichen Mehraufwand ohne Nutzen.|  
|[CA1822: Member als statisch markieren](../code-quality/ca1822-mark-members-as-static.md)|Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden \(Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus.  Dies kann zu einer messbaren Leistungssteigerung für leistungsabhängigen Code führen.|  
|[CA1823: Nicht verwendete private Felder vermeiden](../code-quality/ca1823-avoid-unused-private-fields.md)|Es wurden private Felder erkannt, auf die in der Assembly anscheinend kein Zugriff erfolgt.|  
|[CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Mit dem NeutralResourcesLanguage\-Attribut wird dem ResourceManager die Sprache mitgeteilt, in der die Ressourcen einer neutralen Kultur für eine Assembly angezeigt wurden.  Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern.|
---
title: "CA1812: Nicht instanziierte interne Klassen vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1812"
  - "AvoidUninstantiatedInternalClasses"
helpviewer_keywords: 
  - "AvoidUninstantiatedInternalClasses"
  - "CA1812"
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 26
---
# CA1812: Nicht instanziierte interne Klassen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUninstantiatedInternalClasses|  
|CheckId|CA1812|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt.  
  
## Regelbeschreibung  
 Diese Regel versucht, einen Aufruf eines der Konstruktoren des Typs zu finden, und meldet einen Verstoß, wenn kein Aufruf gefunden wird.  
  
 Die folgenden Typen werden durch diese Regel nicht überprüft:  
  
-   Werttypen  
  
-   Abstrakte Typen  
  
-   Enumerationen  
  
-   Delegaten  
  
-   Von einem Compiler ausgegebene Arraytypen  
  
-   Typen, die nicht instanziiert werden können und nur `static` Methoden \(`Shared` in Visual Basic\) definieren.  
  
 Wenn Sie <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> auf die zu analysierende Assembly anwenden, wird diese Regel nicht für Konstruktoren ausgelöst, die mit `internal` markiert sind, da nicht zu erkennen ist, ob ein Feld von einer anderen `friend`\-Assembly verwendet wird.  
  
 Obwohl es keine Möglichkeit gibt, diese Einschränkung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Codeanalyse zu umgehen, wird der externe eigenständige FxCop\-Prozess für interne Konstruktoren ausgelöst, wenn die einzelnen `friend`\-Assemblys in der Analyse vorhanden sind.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Typ, oder fügen Sie den Code hinzu, in dem der Typ verwendet wird.  Wenn der Typ nur statische Methoden enthält, fügen Sie dem Typ eines der folgenden Elemente hinzu, um den Compiler daran zu hindern, einen Standardkonstruktor für eine öffentliche Instanz auszugeben:  
  
-   Einen privaten Konstruktor für Typen, die auf [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Version 1.0 und 1.1, abzielen.  
  
-   Der `static`\-Modifizierer \(`Shared` in Visual Basic\) für Typen, die auf [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] abzielen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden.  Es wird empfohlen, diese Warnung in den folgenden Situationen zu unterdrücken:  
  
-   Die Klasse wird durch spät gebundene Reflektionsmethoden wie <xref:System.Activator.CreateInstance?displayProperty=fullName> erstellt.  
  
-   Die Klasse wird automatisch durch die Laufzeit oder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] erstellt.  Beispielsweise Klassen, die <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> oder <xref:System.Web.IHttpHandler?displayProperty=fullName> implementieren.  
  
-   Die Klasse wird als generischer Typparameter mit einer neuen Einschränkung übergeben.  Im folgenden Beispiel wird z. B. diese Regel ausgelöst:  
  
    ```c#  
    internal class MyClass  
    {     
        public DoSomething()     
        {  
        }  
    }   
    public class MyGeneric<T> where T : new()  
    {  
        public T Create()  
        {  
            return new T();     
        }  
    }  
    // [...]   
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();  
    mc.Create();  
    ```  
  
 Die Empfehlung für diese Situationen lautete, die Warnung zu unterdrücken.  
  
## Verwandte Regeln  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
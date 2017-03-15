---
title: "CA1058: Typen sollten bestimmte Basistypen nicht erweitern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1058: Typen sollten bestimmte Basistypen nicht erweitern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein extern sichtbarer Typ erweitert bestimmte Basistypen.  Derzeit meldet diese Regel Typen, die sich von folgenden Typen ableiten:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## Regelbeschreibung  
 Für [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Version 1, wurde empfohlen, neue Ausnahmen von <xref:System.ApplicationException> abzuleiten.  Die Empfehlung hat sich geändert: Nun sollten neue Ausnahmen von <xref:System.Exception?displayProperty=fullName> oder einer der zugehörigen Unterklassen im <xref:System>\-Namespace abgeleitet werden.  
  
 Erstellen Sie keine Unterklasse von <xref:System.Xml.XmlDocument>, wenn Sie eine XML\-Ansicht eines zugrunde liegenden Objektmodells oder einer Datenquelle erstellen möchten.  
  
### Nicht generische Auflistungen  
 Verwenden und\/oder erweitern Sie nach Möglichkeit generische Auflistungen.  Erweitern Sie keine nicht generischen Auflistungen im Code, sofern sie nicht zuvor gesendet wurden.  
  
 **Beispiele für falsche Verwendung**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Beispiele für richtige Verwendung**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ von einem anderen Basistyp oder einer generischen Auflistung ab.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie bei Verstößen in Zusammenhang mit <xref:System.ApplicationException> keine Warnung dieser Regel.  Warnungen dieser Regel können gefahrlos für Verstöße im Zusammenhang mit <xref:System.Xml.XmlDocument> unterdrückt werden.  Eine Warnung über eine nicht generische Auflistung kann gefahrlos unterdrückt werden, wenn der Code zuvor freigegeben wurde.
---
title: 'CA1058: Typen sollten bestimmte Basistypen nicht erweitern | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70d7ec2767542db8e38d60198b5f00554897e4ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typen sollten bestimmte Basistypen nicht erweitern
|||  
|-|-|  
|TypeName|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein extern sichtbarer Typ erweitert bestimmte Basistypen. Diese Regel meldet derzeit, Typen, die von den folgenden Typen abgeleitet werden:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Für [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , Version 1, wurde empfohlen, neue Ausnahmen von abzuleiten <xref:System.ApplicationException>. Die Empfehlung hat sich geändert und eine neue Ausnahmen sollten Ableitung <xref:System.Exception?displayProperty=fullName> oder einer seiner Unterklassen in der <xref:System> Namespace.  
  
 Erstellen Sie eine Unterklasse von nicht <xref:System.Xml.XmlDocument> , wenn Sie eine XML-Sicht der zugrunde liegenden Modell oder die Datenquelle erstellen möchten.  
  
### <a name="non-generic-collections"></a>Nicht generische Auflistungen  
 Erweitern Sie generische Auflistungen möglichst und/oder verwendet. Nicht generische Auflistungen in Ihrem Code können nicht erweitert werden, es sei denn, die Sie zuvor exportiert haben.  
  
 **Beispiele für die falsche Verwendung**  
  
```csharp  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Beispiele für die richtige Verwendung**  
  
```csharp  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ in einen anderen Basistyp oder einer generischen Auflistung ein.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel Verstöße zu <xref:System.ApplicationException>. Unterdrücken Sie eine Warnung dieser Regel Verstöße zu kann gefahrlos <xref:System.Xml.XmlDocument>. Sie können ruhig So unterdrücken Sie eine Warnung über eine nicht generische Auflistung, wenn der Code zuvor veröffentlicht wurden.
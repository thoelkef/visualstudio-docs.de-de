---
title: 'CA1058: Typen sollten bestimmte Basis Typen nicht erweitern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9a4663fe3bc09b27bad9eeec05e325f07a3de6f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603065"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typen sollten bestimmte Basistypen nicht erweitern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ erweitert bestimmte Basistypen. Zurzeit meldet diese Regel Typen, die von den folgenden Typen abgeleitet sind:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung
 Für [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Version 1 wurde empfohlen, dass Sie neue Ausnahmen von <xref:System.ApplicationException> ableiten. Die Empfehlung wurde geändert, und neue Ausnahmen sollten von <xref:System.Exception?displayProperty=fullName> oder einer ihrer Unterklassen im <xref:System>-Namespace abgeleitet werden.

 Erstellen Sie keine Unterklasse von <xref:System.Xml.XmlDocument>, wenn Sie eine XML-Sicht eines zugrunde liegenden Objektmodells oder einer zugrunde liegenden Datenquelle erstellen möchten.

### <a name="non-generic-collections"></a>Nicht generische Auflistungen
 Verwenden Sie nach Möglichkeit und/oder erweitern Sie generische Auflistungen. Erweitern Sie keine nicht generischen Auflistungen in Ihrem Code, es sei denn, Sie haben Sie zuvor versendet.

 **Beispiele für falsche Verwendung**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Beispiele für die korrekte Verwendung**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ von einem anderen Basistyp oder einer generischen Auflistung ab.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel auf Verstöße gegen <xref:System.ApplicationException>. Es ist sicher, bei Verstößen gegen <xref:System.Xml.XmlDocument> eine Warnung aus dieser Regel zu unterdrücken. Es ist sicher, eine Warnung zu einer nicht generischen Auflistung zu unterdrücken, wenn der Code zuvor freigegeben wurde.

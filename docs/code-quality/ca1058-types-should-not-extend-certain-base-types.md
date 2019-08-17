---
title: 'CA1058: Typen sollten bestimmte Basistypen nicht erweitern.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38d92194a5aa2b46a0cb65a1525bc01d9de67b86
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547356"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typen sollten bestimmte Basistypen nicht erweitern.

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ erweitert einen der folgenden Basis Typen:

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Ausnahmen sollten von <xref:System.Exception?displayProperty=fullName> oder einer ihrer Unterklassen <xref:System> im-Namespace abgeleitet werden.

Erstellen Sie keine Unterklasse von <xref:System.Xml.XmlDocument> , wenn Sie eine XML-Sicht eines zugrunde liegenden Objektmodells oder einer zugrunde liegenden Datenquelle erstellen möchten.

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

Unterdrücken Sie keine Warnung aus dieser Regel auf Verstöße <xref:System.ApplicationException>gegen. Es ist sicher, bei Verstößen <xref:System.Xml.XmlDocument>gegen eine Warnung aus dieser Regel zu unterdrücken. Es ist sicher, eine Warnung zu einer nicht generischen Auflistung zu unterdrücken, wenn der Code zuvor freigegeben wurde.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).
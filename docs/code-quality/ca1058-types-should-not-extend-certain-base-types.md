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
ms.openlocfilehash: 4157316756e4b180f6fb49082bf60927ddb43707
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714796"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typen sollten bestimmte Basistypen nicht erweitern.

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ erweitert eine der folgenden Basistypen:

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

Diese Regel nur sucht standardmäßig an extern sichtbare Typen, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Ausnahmen sollten abgeleitet <xref:System.Exception?displayProperty=fullName> oder eine ihrer Unterklassen in die <xref:System> Namespace.

Erstellen Sie eine Unterklasse von nicht <xref:System.Xml.XmlDocument> sollten Sie eine XML-Ansicht der zugrunde liegenden Modell oder die Datenquelle zu erstellen.

### <a name="non-generic-collections"></a>Nicht generische Auflistungen

Verwenden Sie und/oder Erweitern von generischen Auflistungen, wann immer möglich. Nicht generische Auflistungen in Ihrem Code können nicht erweitert werden, es sei denn, die Sie bereits geliefert haben.

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

Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ von einem unterschiedlichen Basistyp oder einer generischen Auflistung ein.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel für Verstöße zu <xref:System.ApplicationException>. Es ist sicherer, unterdrücken Sie eine Warnung dieser Regel Verstöße zu <xref:System.Xml.XmlDocument>. Es ist sicher, um eine Warnung über eine nicht generische Auflistung zu unterdrücken, wenn der Code zuvor veröffentlicht wurden.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).
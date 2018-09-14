---
title: 'CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04e8348dc77222fbc06887efebf44c735eb7c8f0
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550020"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen
|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Extern sichtbaren Members eines bestimmten konkreten Typs ist, macht bestimmte konkreten Typen durch einen seiner Parameter oder Rückgabewert. Diese Regel meldet derzeit Offenlegung der folgenden konkrete Typen:

- Ein abgeleiteter Typ von <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 Ein konkreter Typ ist ein Typ, der eine vollständige Implementierung aufweist und deshalb instanziiert werden kann. Damit wird der Member universell verwendet, ersetzen Sie den konkreten Typ durch die vorgeschlagene Schnittstelle. Dadurch wird das Element akzeptiert jeden Typ, der die Schnittstelle implementiert oder verwendet werden, wenn ein Typ, der die Schnittstelle implementiert erwartet wird.

 Die folgende Tabelle enthält die entsprechenden konkreten Typen und ihre vorgeschlagenen Ersetzungen.

|Konkreten Typ|Ersetzung|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName><br /><br /> Mithilfe der Benutzeroberfläche entkoppelt das Element aus einer bestimmten Implementierung von einer XML-Datenquelle.|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den konkreten Typ, auf die vorgeschlagene Schnittstelle.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, um eine Meldung von dieser Regel zu unterdrücken, wenn die spezifische Funktionen durch den konkreten Typ erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1011: Basistypen als Parameter übergeben](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
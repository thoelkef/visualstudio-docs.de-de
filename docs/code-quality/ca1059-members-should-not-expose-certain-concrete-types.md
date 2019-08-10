---
title: 'CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f24881d04599677c5d45c93fc940286f115d593
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922513"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen.

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein extern sichtbarer Member ist ein bestimmter konkreter Typ oder macht bestimmte konkrete Typen über einen seiner Parameter oder Rückgabewerte verfügbar. Zurzeit meldet diese Regel die verfügbar machung der folgenden konkreten Typen:

- Ein von <xref:System.Xml.XmlNode?displayProperty=fullName>abgeleiteter Typ.

## <a name="rule-description"></a>Regelbeschreibung
Ein konkreter Typ ist ein Typ, der eine vollständige Implementierung aufweist und deshalb instanziiert werden kann. Um die weit verbreitete Verwendung des Members zuzulassen, ersetzen Sie den konkreten Typ durch die vorgeschlagene Schnittstelle. Dadurch kann der Member jeden Typ akzeptieren, der die-Schnittstelle implementiert oder verwendet wird, wenn ein Typ erwartet wird, der die-Schnittstelle implementiert.

In der folgenden Tabelle sind die gezielten konkreten Typen und deren vorgeschlagene Ersetzung aufgeführt.

|Konkreter Typ|Ersetzung|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName><br /><br /> Durch die Verwendung der-Schnittstelle wird der Member von einer bestimmten Implementierung einer XML-Datenquelle entkoppelt.|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den konkreten Typ in die vorgeschlagene Schnittstelle.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Nachricht aus dieser Regel zu unterdrücken, wenn die vom konkreten Typ bereitgestellte spezifische Funktionalität erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln
[CA1011: Übergeben von Basis Typen als Parameter](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
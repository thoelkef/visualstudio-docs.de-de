---
title: 'CA1059: Member sollten bestimmte konkreten Typen nicht verfügbar | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a78125645dc6369811b4b9e1d7101b7bb4cbba76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200490"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, um eine Meldung von dieser Regel zu unterdrücken, wenn die spezifische Funktionen durch den konkreten Typ erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1011: Betrachten Sie Basistypen als Parameter übergeben.](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)

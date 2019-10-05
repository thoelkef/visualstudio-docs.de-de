---
title: 'CA2212: ServicedComponents nicht mit WebMethod markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b2ace5f6e51fc7a8d29faab14cc2332fd808f93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231652"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: ServicedComponents nicht mit WebMethod markieren.

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode in einem Typ, der von <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> erbt, ist mit <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>markiert.

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.Web.Services.WebMethodAttribute>gilt für Methoden innerhalb eines XML-Webdiensts, die mit ASP.NET erstellt wurden. Dadurch kann die Methode von Remoteweb Clients aufgerufen werden. Die-Methode und die-Klasse müssen öffentlich sein und in einer ASP.NET-Webanwendung ausgeführt werden. <xref:System.EnterpriseServices.ServicedComponent>Typen werden von com+-Anwendungen gehostet und können com+-Dienste verwenden. <xref:System.Web.Services.WebMethodAttribute>wird nicht auf- <xref:System.EnterpriseServices.ServicedComponent> Typen angewendet, da Sie nicht für dieselben Szenarien vorgesehen sind. Insbesondere wird durch das Hinzufügen des <xref:System.EnterpriseServices.ServicedComponent> -Attributs zur-Methode nicht die Methode von Remoteweb Clients aufgerufen. Da <xref:System.Web.Services.WebMethodAttribute> und eine <xref:System.EnterpriseServices.ServicedComponent> Methode widersprüchliche Verhalten und Anforderungen für den Kontext-und Transaktions Fluss aufweisen, ist das Verhalten der Methode in einigen Szenarien falsch.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das- <xref:System.EnterpriseServices.ServicedComponent> Attribut aus der-Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel. Es gibt keine Szenarios, in denen die Kombination dieser Elemente korrekt ist.

## <a name="see-also"></a>Siehe auch

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
---
title: 'CA2212: Serviced Components nicht mit WebMethod markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ee166f8bbc14e66968cd4f7c265331854905ac9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662949"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: ServicedComponents nicht mit WebMethod markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode in einem Typ, der von <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> erbt, ist mit <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> markiert.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Web.Services.WebMethodAttribute> gilt für Methoden innerhalb eines XML-Webdiensts, die mit ASP.NET erstellt wurden. Dadurch kann die Methode von Remoteweb Clients aufgerufen werden. Die-Methode und die-Klasse müssen öffentlich sein und in einer ASP.NET-Webanwendung ausgeführt werden. <xref:System.EnterpriseServices.ServicedComponent>-Typen werden von com+-Anwendungen gehostet und können com+-Dienste verwenden. <xref:System.Web.Services.WebMethodAttribute> wird nicht auf <xref:System.EnterpriseServices.ServicedComponent>-Typen angewendet, da Sie nicht für dieselben Szenarios vorgesehen sind. Durch das Hinzufügen des-Attributs zur <xref:System.EnterpriseServices.ServicedComponent>-Methode wird die Methode nicht von Remoteweb Clients aufgerufen. Da <xref:System.Web.Services.WebMethodAttribute> und eine <xref:System.EnterpriseServices.ServicedComponent>-Methode widersprüchliche Verhalten und Anforderungen für den Kontext und den Transaktions Fluss aufweisen, ist das Verhalten der Methode in einigen Szenarien falsch.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das-Attribut aus der <xref:System.EnterpriseServices.ServicedComponent>-Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Es gibt keine Szenarios, in denen die Kombination dieser Elemente korrekt ist.

## <a name="see-also"></a>Siehe auch
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>

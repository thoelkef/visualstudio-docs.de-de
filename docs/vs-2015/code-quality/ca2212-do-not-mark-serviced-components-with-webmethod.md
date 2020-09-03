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
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534562"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: ServicedComponents nicht mit WebMethod markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode in einem Typ, der von erbt, <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> ist mit markiert <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 <xref:System.Web.Services.WebMethodAttribute> gilt für Methoden innerhalb eines XML-Webdiensts, die mit ASP.NET erstellt wurden. Dadurch kann die Methode von Remoteweb Clients aufgerufen werden. Die-Methode und die-Klasse müssen öffentlich sein und in einer ASP.NET-Webanwendung ausgeführt werden. <xref:System.EnterpriseServices.ServicedComponent> Typen werden von com+-Anwendungen gehostet und können com+-Dienste verwenden. <xref:System.Web.Services.WebMethodAttribute> wird nicht auf- <xref:System.EnterpriseServices.ServicedComponent> Typen angewendet, da Sie nicht für dieselben Szenarien vorgesehen sind. Insbesondere wird durch das Hinzufügen des-Attributs zur- <xref:System.EnterpriseServices.ServicedComponent> Methode nicht die Methode von Remoteweb Clients aufgerufen. Da <xref:System.Web.Services.WebMethodAttribute> und eine <xref:System.EnterpriseServices.ServicedComponent> Methode widersprüchliche Verhalten und Anforderungen für den Kontext-und Transaktions Fluss aufweisen, ist das Verhalten der Methode in einigen Szenarien falsch.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das-Attribut aus der- <xref:System.EnterpriseServices.ServicedComponent> Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Es gibt keine Szenarios, in denen die Kombination dieser Elemente korrekt ist.

## <a name="see-also"></a>Weitere Informationen
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>

---
title: 'CA2212: ServicedComponents mit WebMethod nicht markieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 33f23ead1a4236c60e8c152f5064d6d1b6f4d3b3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589613"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: ServicedComponents nicht mit WebMethod markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2212: ServicedComponents mit WebMethod nicht markieren](https://docs.microsoft.com/visualstudio/code-quality/ca2212-do-not-mark-serviced-components-with-webmethod).

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode in einem Typ, der von erbt <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> ist mit markiert <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Web.Services.WebMethodAttribute> gilt für Methoden innerhalb eines XML-Webdiensts, die mit ASP.NET erstellt wurden. Dadurch kann die Methode von Remotewebclients aufgerufen. Der Methode und die Klasse müssen öffentlich sein und in einer ASP.NET Web-Anwendung ausgeführt werden. <xref:System.EnterpriseServices.ServicedComponent> Typen von COM+-Anwendungen gehostet werden, und COM+-Dienste verwenden können. <xref:System.Web.Services.WebMethodAttribute> gilt nicht für <xref:System.EnterpriseServices.ServicedComponent> Typen, da sie nicht für die gleichen Szenarien vorgesehen sind. Insbesondere Hinzufügen des Attributs auf die <xref:System.EnterpriseServices.ServicedComponent> -Methode nicht, dass die Methode aufgerufen aus. Da <xref:System.Web.Services.WebMethodAttribute> und <xref:System.EnterpriseServices.ServicedComponent> Methode in Konflikt stehenden Verhalten und Anforderungen für den Kontext, Transaktionsfluss und das Verhalten der Methode werden in bestimmten Szenarien fehlerhaft.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Attribut aus der <xref:System.EnterpriseServices.ServicedComponent> Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Es gibt keine Szenarios, in denen eine Kombination aus diesen Elementen korrekt ist.

## <a name="see-also"></a>Siehe auch
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>




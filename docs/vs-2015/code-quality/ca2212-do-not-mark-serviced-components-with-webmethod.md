---
title: 'CA2212: Nicht verarbeitete Komponenten mit WebMethod markieren | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6f2e89705e36407e39103296e3eee70482e3d03f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142484"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: ServicedComponents nicht mit WebMethod markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

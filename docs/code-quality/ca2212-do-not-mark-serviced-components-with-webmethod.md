---
title: 'CA2212: ServicedComponents nicht mit WebMethod markieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d2e2790db4a3e8061dcd949b79c127e67f022d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: ServicedComponents nicht mit WebMethod markieren
|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode in einem Typ, der von erbt <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> mit RuntimeCompatibility <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Web.Services.WebMethodAttribute> gilt für Methoden in einem XML-Webdienst, die mithilfe von ASP.NET erstellt wurden. Es wird die Methode von Remotewebclients aufgerufen werden kann. Die Methode und die Klasse müssen öffentlich sein und in einer ASP.NET Web-Anwendung ausgeführt werden. <xref:System.EnterpriseServices.ServicedComponent> Typen von COM+-Anwendungen gehostet werden und COM+-Dienste verwenden können. <xref:System.Web.Services.WebMethodAttribute> gilt nicht für <xref:System.EnterpriseServices.ServicedComponent> Typen, da sie nicht den gleichen Fällen bestimmt sind. Insbesondere das-Attribut hinzufügen der <xref:System.EnterpriseServices.ServicedComponent> -Methode nicht, dass die Methode aufgerufen werden kann von remote-Web-Clients. Da <xref:System.Web.Services.WebMethodAttribute> und eine <xref:System.EnterpriseServices.ServicedComponent> Methode verfügen, in Konflikt stehenden Verhalten und Anforderungen für den Kontext, die einen Transaktionsfluss und das Verhalten der Methode werden in einigen Szenarien falsch sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Attribut aus der <xref:System.EnterpriseServices.ServicedComponent> Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Es gibt keine Szenarien, in dem eine Kombination dieser Elemente richtig ist.

## <a name="see-also"></a>Siehe auch
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
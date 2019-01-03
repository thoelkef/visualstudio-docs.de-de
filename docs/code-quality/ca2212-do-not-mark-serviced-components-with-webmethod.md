---
title: 'CA2212: Nicht verarbeitete Komponenten mit WebMethod markieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 402e27bcfb94adc73aa5376ca71271e8d55f5d8d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856669"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Nicht verarbeitete Komponenten mit WebMethod markieren

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode in einem Typ, der von erbt <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> ist mit markiert <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.Web.Services.WebMethodAttribute> gilt für Methoden innerhalb eines XML-Webdiensts, die mit ASP.NET erstellt wurden. Dadurch kann die Methode von remote-Web-Clients aufgerufen. Die Methode und die Klasse muss öffentlich und Ausführung in einer ASP.NET-Webanwendung. <xref:System.EnterpriseServices.ServicedComponent> Typen von COM+-Anwendungen gehostet werden, und COM+-Dienste verwenden können. <xref:System.Web.Services.WebMethodAttribute> gilt nicht für <xref:System.EnterpriseServices.ServicedComponent> Typen, da sie nicht für die gleichen Szenarien vorgesehen sind. Insbesondere Hinzufügen des Attributs auf die <xref:System.EnterpriseServices.ServicedComponent> -Methode nicht, dass die Methode aufgerufen von remote-Web-Clients. Da <xref:System.Web.Services.WebMethodAttribute> und <xref:System.EnterpriseServices.ServicedComponent> Methode in Konflikt stehenden Verhalten und Anforderungen für den Kontext, Transaktionsfluss und das Verhalten der Methode werden in bestimmten Szenarien fehlerhaft.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Attribut aus der <xref:System.EnterpriseServices.ServicedComponent> Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel. Es gibt keine Szenarios, in denen eine Kombination aus diesen Elementen korrekt ist.

## <a name="see-also"></a>Siehe auch

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
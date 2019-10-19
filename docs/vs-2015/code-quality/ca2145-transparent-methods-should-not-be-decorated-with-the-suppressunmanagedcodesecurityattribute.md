---
title: 'CA2145: transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurityAttribute-Attribut versehen werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6bffa680fa39014ffa96feec997b5eca63ee08ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610208"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Transparentmethodsschulter dnotusesuppressunmanagedcodesecurity|
|CheckId|CA2145|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode, eine Methode, die mit der <xref:System.Security.SecuritySafeCriticalAttribute>-Methode gekennzeichnet ist, oder ein Typ, der eine-Methode enthält, wird mit dem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>-Attribut gekennzeichnet.

## <a name="rule-description"></a>Regelbeschreibung
 Methoden, die mit dem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>-Attribut ergänzt werden, haben einen impliziten LinkDemand, der auf jede Methode angewendet wird, die Sie aufruft Dieser LinkDemand erfordert, dass der aufrufende Code sicherheitskritisch ist. Das Markieren der Methode, die SuppressUnmanagedCodeSecurity mit dem <xref:System.Security.SecurityCriticalAttribute>-Attribut verwendet, macht diese Anforderung für Aufrufer der-Methode deutlicher.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode oder den Typ mit dem <xref:System.Security.SecurityCriticalAttribute>-Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Kommentare

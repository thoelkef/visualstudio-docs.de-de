---
title: 'CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6808c5e9b5d35ab6ec8d4012f08e15cba9a159d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920570"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.

|||
|-|-|
|TypeName|Transparentmethodsmustnothandleprocesscorruptingexceptions|
|CheckId|CA2139|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine transparente Methode wird mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut gekennzeichnet.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel löst eine beliebige Methode aus, die transparent ist und versucht, eine Prozess beschädigte Ausnahme mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut zu behandeln. Eine Ausnahme bei der Prozess Beschädigung ist eine CLR-Version 4,0-Ausnahme Klassifizierung <xref:System.AccessViolationException>von Ausnahmen. Das HandleProcessCorruptedStateExceptionsAttribute-Attribut darf nur von sicherheitskritischen Methoden verwendet werden und wird ignoriert, wenn es für eine transparente Methode übernommen wird. Um Prozess beschädigte Ausnahmen zu verarbeiten, muss diese Methode sicherheitskritisch oder sicherheitsrelevant sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, entfernen <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Sie das-Attribut, oder markieren Sie <xref:System.Security.SecurityCriticalAttribute> die Methode <xref:System.Security.SecuritySafeCriticalAttribute> mit dem-Attribut oder dem-Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
In diesem Beispiel wird eine transparente Methode mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut markiert, und die Regel schlägt fehl. Die-Methode sollte auch mit dem <xref:System.Security.SecurityCriticalAttribute> -Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute> -Attribut gekennzeichnet sein.

[!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]
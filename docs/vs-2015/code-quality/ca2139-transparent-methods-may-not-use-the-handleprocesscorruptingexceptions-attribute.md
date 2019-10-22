---
title: 'CA2139: transparente Methoden dürfen das "processprocesscorruptingexceptions"-Attribut nicht verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 821598d7708fa8681f1dbc5fee65978d7498dbb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602992"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Transparentmethodsmustnothandleprocesscorruptingexceptions|
|CheckId|CA2139|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode wird mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>-Attribut gekennzeichnet.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel löst eine beliebige Methode aus, die transparent ist und versucht, eine Prozess beschädigte Ausnahme mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>-Attribut zu behandeln. Eine Ausnahme bei der Prozess Beschädigung ist eine CLR-Version 4,0-Ausnahme Klassifizierung von Ausnahmen, z. b. <xref:System.AccessViolationException>. Das HandleProcessCorruptedStateExceptionsAttribute-Attribut darf nur von sicherheitskritischen Methoden verwendet werden und wird ignoriert, wenn es für eine transparente Methode übernommen wird. Um Prozess beschädigte Ausnahmen zu verarbeiten, muss diese Methode sicherheitskritisch oder sicherheitsrelevant sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>-Attribut, oder markieren Sie die Methode mit dem <xref:System.Security.SecurityCriticalAttribute> oder dem <xref:System.Security.SecuritySafeCriticalAttribute>-Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird eine transparente Methode mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>-Attribut markiert, und die Regel schlägt fehl. Die-Methode sollte auch mit dem-<xref:System.Security.SecurityCriticalAttribute> oder dem <xref:System.Security.SecuritySafeCriticalAttribute>-Attribut markiert werden.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]

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
ms.openlocfilehash: ea4f9dc11d2cbb3100ca6e2e0b3177b1acec923a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173557"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypName|Transparentmethodsmustnothandleprocesscorruptingexceptions|
|CheckId|CA2139|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode wird mit dem- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut gekennzeichnet.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel löst eine beliebige Methode aus, die transparent ist und versucht, eine Prozess beschädigte Ausnahme mit dem-Attribut zu behandeln <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> . Eine Ausnahme bei der Prozess Beschädigung ist eine CLR-Version 4,0-Ausnahme Klassifizierung von Ausnahmen <xref:System.AccessViolationException> . Das HandleProcessCorruptedStateExceptionsAttribute-Attribut darf nur von sicherheitskritischen Methoden verwendet werden und wird ignoriert, wenn es für eine transparente Methode übernommen wird. Um Prozess beschädigte Ausnahmen zu verarbeiten, muss diese Methode sicherheitskritisch oder sicherheitsrelevant sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut, oder markieren Sie die Methode mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut oder dem- <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird eine transparente Methode mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut markiert, und die Regel schlägt fehl. Die-Methode sollte auch mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut oder dem-Attribut gekennzeichnet sein <xref:System.Security.SecuritySafeCriticalAttribute> .

 [!code-csharp[FxCop.Security.CA2139#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139/cs/ca2139.cs#1)]

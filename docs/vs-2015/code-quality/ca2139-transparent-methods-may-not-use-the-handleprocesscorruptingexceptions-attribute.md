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
ms.openlocfilehash: 233e4366befd2a5a0d5690b14198ac13e2fcc957
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546483"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|Transparentmethodsmustnothandleprocesscorruptingexceptions|
|CheckId|CA2139|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode wird mit dem- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut gekennzeichnet.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel löst eine beliebige Methode aus, die transparent ist und versucht, eine Prozess beschädigte Ausnahme mit dem-Attribut zu behandeln <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> . Eine Ausnahme bei der Prozess Beschädigung ist eine CLR-Version 4,0-Ausnahme Klassifizierung von Ausnahmen <xref:System.AccessViolationException> . Das HandleProcessCorruptedStateExceptionsAttribute-Attribut darf nur von sicherheitskritischen Methoden verwendet werden und wird ignoriert, wenn es für eine transparente Methode übernommen wird. Um Prozess beschädigte Ausnahmen zu verarbeiten, muss diese Methode sicherheitskritisch oder sicherheitsrelevant sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut, oder markieren Sie die Methode mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut oder dem- <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird eine transparente Methode mit dem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> -Attribut markiert, und die Regel schlägt fehl. Die-Methode sollte auch mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut oder dem-Attribut gekennzeichnet sein <xref:System.Security.SecuritySafeCriticalAttribute> .

 [!code-csharp[FxCop.Security.CA2139#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139/cs/ca2139.cs#1)]

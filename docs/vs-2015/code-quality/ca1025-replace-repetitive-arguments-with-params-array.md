---
title: 'CA1025: sich wiederholende Argumente durch ein Parameter Array ersetzen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 84809341d7898aeb3defe0447f2a2f1142eb460a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546626"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ weist mehr als drei Parameter auf, und die letzten drei Parameter weisen denselben Typ auf.

## <a name="rule-description"></a>Beschreibung der Regel
 Verwenden Sie ein Parameter Array anstelle von wiederholten Argumenten, wenn die genaue Anzahl der Argumente unbekannt ist und die Variablen Argumente denselben Typ aufweisen oder als derselbe Typ übergeben werden können. Die-Methode stellt z. b <xref:System.Console.WriteLine%2A> . eine allgemeine Überladung bereit, die ein Parameter Array verwendet, um eine beliebige Anzahl von Argumenten zu akzeptieren <xref:System.Object> .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die wiederholten Argumente durch ein Parameter Array.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist immer sicher, eine Warnung aus dieser Regel zu unterdrücken. Dieser Entwurf kann jedoch Probleme mit der Benutzerfreundlichkeit verursachen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]

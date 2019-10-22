---
title: 'CA2200: erneut auslösen, um Stapel Details beizubehalten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d20407d7cc708ac785e4a792bf8e64768ea58540
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667391"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Erneut ausführen, um Stapeldetails beizubehalten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird explizit in der `throw`-Anweisung angegeben.

## <a name="rule-description"></a>Regelbeschreibung
 Sobald eine Ausnahme ausgelöst wird, ist ein Teil der Informationen, die er enthält, die Stapel Überwachung. Die Stapel Überwachung ist eine Liste der Methoden Aufrufhierarchie, die mit der-Methode beginnt, die die Ausnahme auslöst und mit der-Methode endet, die die Ausnahme abfängt. Wenn eine Ausnahme erneut ausgelöst wird, indem die Ausnahme in der `throw`-Anweisung angegeben wird, wird die Stapel Überwachung bei der aktuellen Methode neu gestartet, und die Liste der Methodenaufrufe zwischen der ursprünglichen Methode, die die Ausnahme ausgelöst hat, und der aktuellen Methode gehen verloren. Um die ursprünglichen Stapel Verfolgungs Informationen mit der Ausnahme beizubehalten, verwenden Sie die `throw`-Anweisung, ohne die Ausnahme anzugeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, lösen Sie die Ausnahme erneut aus, ohne die Ausnahme explizit anzugeben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, `CatchAndRethrowExplicitly`, die gegen die Regel verstößt, und eine Methode, `CatchAndRethrowImplicitly`, die die Regel erfüllt.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]

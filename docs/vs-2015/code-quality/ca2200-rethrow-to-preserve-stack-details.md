---
title: 'CA2200: Rethrow um Stapeldetails beizubehalten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5a79dd4f12a2d97cb707a38f4a46e5a20a8436b1
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589957"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Erneut ausführen, um Stapeldetails beizubehalten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2200: Rethrow um Stapeldetails beizubehalten](https://docs.microsoft.com/visualstudio/code-quality/ca2200-rethrow-to-preserve-stack-details).

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Ausnahme wird erneut ausgelöst wird und die Ausnahme wird explizit angegeben, der `throw` Anweisung.

## <a name="rule-description"></a>Regelbeschreibung
 Sobald eine Ausnahme ausgelöst wird, ist Teil der Informationen, die es enthält die stapelüberwachung. Die stapelüberwachung ist eine Liste von der Methode Aufrufhierarchie, die mit der Methode beginnt, die die Ausnahme auslöst, und endet mit der Methode, die die Ausnahme abgefangen. Wenn eine Ausnahme erneut ausgelöst wird, durch Angeben der Ausnahme in der `throw` -Anweisung, die stapelüberwachung auf die aktuelle Methode neu gestartet wird und die Liste der Methodenaufrufe zwischen der ursprünglichen Methode, die die Ausnahme ausgelöst hat und die aktuelle Methode geht verloren. Um die ursprüngliche Stapelüberwachungsinformationen mit der Ausnahme zu halten, verwenden Sie die `throw` -Anweisung ohne Angabe der Ausnahme.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen lösen Sie die Ausnahme erneut ohne Angabe der Ausnahme explizit aus.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, `CatchAndRethrowExplicitly`, die gegen die Regel und eine Methode, `CatchAndRethrowImplicitly`, die die Regel erfüllt.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]




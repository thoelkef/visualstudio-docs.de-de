---
title: 'CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 910be06a7d9897f306b6bb2b89ca99b733623faf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen
|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|CheckId|CA1025|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ über mehr als drei Parameter verfügt, und die letzten drei Parameter sind vom gleichen Typ.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Verwenden Sie ein Parameterarray statt sich wiederholender Argumente, wenn die genaue Anzahl von Argumenten unbekannt ist, und die Variablenargumenten denselben Typ aufweisen oder als gleicher Typ übergeben werden können. Z. B. die <xref:System.Console.WriteLine%2A> Methode bietet eine allgemeine Überladung, die ein Parameterarray verwendet wird, um eine beliebige Anzahl von akzeptieren <xref:System.Object> Argumente.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die wiederholender Argumente durch ein Parameterarray aus.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig immer zum Unterdrücken einer Warnung dieser Regel; Dieser Entwurf kann jedoch Probleme hinsichtlich der Verwendbarkeit verursachen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der mit dieser Regel verletzt.  
  
 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]
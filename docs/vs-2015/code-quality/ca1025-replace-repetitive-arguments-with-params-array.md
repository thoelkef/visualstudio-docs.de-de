---
title: 'CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b649a5eaa26365fcf7b620ae10db037269716b08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912811"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ über mehr als drei Parameter verfügt und die letzten drei Parameter sind vom gleichen Typ.

## <a name="rule-description"></a>Regelbeschreibung
 Verwenden Sie ein Parameterarray statt sich wiederholender Argumente, wenn die genaue Anzahl von Argumenten unbekannt ist und der Variablen Argumente den gleichen Typ aufweisen oder als gleicher Typ übergeben werden können. Z. B. die <xref:System.Console.WriteLine%2A> Methode bietet eine allgemeine Überladung, die ein Parameterarray verwendet wird, um eine beliebige Anzahl von akzeptieren <xref:System.Object> Argumente.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die wiederholte Argumente mit einem Parameterarray.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicherer, unterdrücken Sie eine Warnung dieser Regel; Dieses Design kann jedoch Probleme hinsichtlich der Verwendbarkeit verursachen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]




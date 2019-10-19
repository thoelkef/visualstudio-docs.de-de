---
title: 'CA2133: Delegaten müssen an Methoden mit einheitlicher Transparenz gebunden werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 487047b7dd3096e65a6e287d79d91d3029f3dc5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608985"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Delegatesmustbindwithkonsistenttransparenz|
|CheckId|CA2133|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

> [!NOTE]
> Diese Warnung wird nur auf Code angewendet, der CoreCLR (die Version der CLR, die für Silverlight-Webanwendungen spezifisch ist) ausgeführt wird.

## <a name="cause"></a>Ursache
 Diese Warnung wird für eine Methode ausgelöst, die einen mit dem <xref:System.Security.SecurityCriticalAttribute> markierten Delegaten an eine Methode bindet, die transparent oder mit der <xref:System.Security.SecuritySafeCriticalAttribute> markiert ist. Die Warnung wird auch für eine Methode ausgelöst, die einen transparenten oder sicherheitsrelevanten Delegaten an eine wichtige Methode bindet.

## <a name="rule-description"></a>Regelbeschreibung
 Delegattypen und die Methoden, an die Sie gebunden werden, müssen über eine konsistente Transparenz verfügen. Transparente und sicherheitskritische Delegaten können nur an andere transparente oder sichere kritische Methoden gebunden werden. Ebenso können kritische Delegaten nur an kritische Methoden gebunden werden. Diese Bindungs Regeln stellen sicher, dass der einzige Code, der eine Methode über einen Delegaten aufrufen kann, auch dieselbe Methode direkt aufgerufen hätte. Bindungs Regeln verhindern z. b., dass transparenter Code kritischen Code direkt über einen transparenten Delegaten aufrufen kann.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Warnung zu beheben, ändern Sie die Transparenz des Delegaten oder der Methode, die gebunden wird, damit die Transparenz der beiden Bindungen gleichwertig ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]

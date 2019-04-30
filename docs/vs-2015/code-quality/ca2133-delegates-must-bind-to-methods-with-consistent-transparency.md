---
title: 'CA2133: Delegaten müssen an Methoden mit konsistenter Transparenz gebunden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a8a19a84336cc6452f663eb65429326b52268728
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386946"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegaten müssen an Methoden mit konsistenter Transparenz gebunden werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

> [!NOTE]
> Diese Warnung wird nur auf Code angewendet werden, die die CoreCLR (die Version der CLR, die speziell für Silverlight-Webanwendungen ist) ausgeführt wird.

## <a name="cause"></a>Ursache
 Diese Warnung wird ausgelöst, auf eine Methode, die einen Delegaten gebunden, die mit der <xref:System.Security.SecurityCriticalAttribute> an eine Methode, die transparent oder mit markiert, die <xref:System.Security.SecuritySafeCriticalAttribute>. Die Warnung wird auch für eine Methode ausgelöst, die einen transparenten oder sicherheitsrelevanten Delegaten an eine wichtige Methode bindet.

## <a name="rule-description"></a>Regelbeschreibung
 Delegattypen und die Methoden, denen sie zum Binden müssen konsistenten Transparenz aufweisen. Transparent und sicher zugänglich Delegaten können nur an andere Methoden transparenten oder sicherheitsrelevanten binden. Auf ähnliche Weise können kritische Delegaten nur an wichtige Methoden gebunden werden. Diese Bindungsregeln stellen Sie sicher, dass der einzige Code, der eine Methode über einen Delegaten aufrufen können auch die gleiche Methode direkt aufgerufen haben kann. Beispielsweise verhindern Bindungsregeln transparenten Code kritischen Code direkt über einen transparenten Delegaten aufrufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Warnung zu beheben, ändern Sie die Transparenz des Delegaten oder der Methode, die es gebunden wird, damit die Transparenz der beiden sind äquivalent.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]

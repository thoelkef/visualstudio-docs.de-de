---
title: 'CA1501: übermäßige Vererbung vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cf797ad67b7df2eb1f3ba1246e965ed6ebbd586d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547861"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Übermäßige Vererbung vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Category|Microsoft. Wartbarkeit|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ ist in seiner Vererbungshierarchie mehr als vier Ebenen tief.

## <a name="rule-description"></a>Beschreibung der Regel
 Tief verschachtelte Typenhierarchien können schwer zu verfolgen, verstehen und verwalten sein. Diese Regel schränkt die Analyse auf Hierarchien im gleichen Modul ein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ von einem Basistyp ab, der in der Vererbungs Hierarchie weniger tief ist, oder entfernen Sie einige der zwischen Basis Typen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Allerdings ist es möglicherweise schwieriger, den Code zu verwalten. Beachten Sie, dass die Behebung von Verstößen gegen diese Regel in Abhängigkeit von der Sichtbarkeit von Basis Typen zu wichtigen Änderungen führen könnte. Beispielsweise ist das Entfernen von öffentlichen Basis Typen eine Breaking Change.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]

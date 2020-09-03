---
title: 'CA1047: geschützte Member in versiegelten Typen nicht deklarieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e115b4d327f1ac45673de491ceaffc90941e1111
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546782"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Geschützte Member in versiegelten Typen nicht deklarieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ ist `sealed` ( `NotInheritable` in Visual Basic) und deklariert einen geschützten Member oder einen geschützten Typ. Diese Regel meldet keine Verstöße gegen <xref:System.Object.Finalize%2A> Methoden, die diesem Muster folgen müssen.

## <a name="rule-description"></a>Beschreibung der Regel
 Typen deklarieren geschützte Member, damit erbende Typen auf den Member zugreifen oder diesen überschreiben können. Definitionsgemäß können Sie nicht von einem versiegelten Typ erben, was bedeutet, dass geschützte Methoden für versiegelte Typen nicht aufgerufen werden können.

 Der c#-Compiler gibt eine Warnung für diesen Fehler aus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene des Members in privat, oder machen Sie den Typ vererbbar.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie den Typ im aktuellen Zustand belassen, kann dies zu Wartungsproblemen führen und bietet keine Vorteile.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]

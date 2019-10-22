---
title: 'CA1064: Ausnahmen sollten öffentlich sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5e704793aeef211ccabd4f2c9993834af205a14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663623"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Ausnahmen sollten öffentlich sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine nicht öffentliche Ausnahme wird direkt von <xref:System.Exception>, <xref:System.SystemException> oder <xref:System.ApplicationException> abgeleitet.

## <a name="rule-description"></a>Regelbeschreibung
 Eine interne Ausnahme ist nur innerhalb Ihres eigenen internen Bereichs sichtbar. Nachdem die Ausnahme den internen Bereich verlassen hat, kann nur die Basisausnahme zum Abfangen der Ausnahme verwendet werden. Wenn die interne Ausnahme von <xref:System.Exception>, <xref:System.SystemException> oder <xref:System.ApplicationException> geerbt wird, verfügt der externe Code nicht über genügend Informationen, um zu wissen, was mit der Ausnahme zu tun ist.

 Wenn der Code jedoch eine öffentliche Ausnahme aufweist, die später als Basis für eine interne Ausnahme verwendet wird, kann davon ausgegangen werden, dass der Code weiter unten mit der Basis Ausnahme intelligent vorgehen kann. Die öffentliche Ausnahme enthält mehr Informationen, als Sie von "t:System.Exception", "t:System.SystemException" oder "t:System.applicationexcep" bereitgestellt werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Legen Sie die Ausnahme als öffentlich fest, oder leiten Sie die interne Ausnahme von einer öffentlichen Ausnahme ab, die nicht <xref:System.Exception>, <xref:System.SystemException> oder <xref:System.ApplicationException> ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Nachricht aus dieser Regel, wenn Sie sicher sind, dass die private Ausnahme innerhalb Ihres eigenen internen Bereichs abgefangen wird.

## <a name="example"></a>Beispiel
 Diese Regel wird für die erste Beispiel Methode, firstcustomexception, ausgelöst, da die Exception-Klasse direkt von der Ausnahme abgeleitet und intern ist. Die Regel wird nicht in der secondcustomexception-Klasse ausgelöst, da die Klasse auch direkt von der Ausnahme abgeleitet ist, wird die Klasse als öffentlich deklariert. Die dritte Klasse führt die Regel auch nicht aus, da Sie nicht direkt von <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName> oder <xref:System.ApplicationException?displayProperty=fullName> abgeleitet ist.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]

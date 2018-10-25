---
title: ': Ca1011 Basistypen als Parameter übergeben | Microsoft-Dokumentation'
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
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a9afb073ef3e722a2a07a05e1ee8629b31b4cfab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898635"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Basistypen als Parameter übergeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methodendeklaration enthält einen formalen Parameter, der ein abgeleiteter Typ ist, und die Methode ruft nur Member der Basisklasse des Parameters.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn in einer Methodendeklaration ein Basistyp als Parameter angegeben wird, kann jeder Typ, der von diesem Basistyp abgeleitet ist, als entsprechendes Argument an die Methode übergeben werden. Wenn das Argument innerhalb des Methodentexts verwendet wird, hängt die spezifische Methode, die ausgeführt wird, der den Typ des Arguments. Wenn die zusätzliche Funktionalität, die vom abgeleiteten Typ bereitgestellt wird, nicht erforderlich ist, ermöglicht die Verwendung des Basistyps allgemeinere Nutzung der Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ des Parameters in den Basistyp.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicherer, unterdrücken Sie eine Warnung dieser Regel

- Wenn die Methode, die bestimmte Funktionen erfordert, die vom abgeleiteten Typ bereitgestellt wird

   \- oder –

- um zu erzwingen, dass nur der abgeleitete Typ oder einen stärker abgeleiteten Typ, an die Methode übergeben wird.

  In diesen Fällen wird der Code sein stabiler aufgrund der starken typüberprüfung, die vom Compiler und Laufzeit bereitgestellt wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, `ManipulateFileStream`, die verwendet werden kann, nur mit einem <xref:System.IO.FileStream> -Objekt, das gegen diese Regel verstößt. Eine zweite Methode, `ManipulateAnyStream`, verstößt die Regel, und Ersetzen Sie dabei die <xref:System.IO.FileStream> Parameter, indem eine <xref:System.IO.Stream>.

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)




---
title: 'CA1301: doppelte Acceleratoren vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 647fef2968971cddb6a14cc19e53eed979b9c151
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661522"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Doppelte Zugriffstasten vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategorie|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ erweitert <xref:System.Windows.Forms.Control?displayProperty=fullName> und enthält mindestens zwei Steuerelemente der obersten Ebene, die über identische Zugriffsschlüssel verfügen, die in einer Ressourcen Datei gespeichert werden.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement unter Verwendung der ALT-TASTE. Wenn mehrere Steuerelemente über doppelte Zugriffstasten verfügen, ist das Verhalten der Zugriffstaste nicht stringent. Möglicherweise ist der Benutzer nicht in der Lage, auf das vorgesehene Steuerelement zuzugreifen, indem er die Zugriffstaste verwendet, und ein anderes als das, was möglicherweise aktiviert ist.

 Die aktuelle Implementierung dieser Regel ignoriert Menü Elemente. Menü Elemente im gleichen Untermenü dürfen jedoch nicht über identische Zugriffstasten verfügen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, definieren Sie eindeutige Zugriffsschlüssel für alle Steuerelemente.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein minimales Formular, das zwei Steuerelemente mit identischen Zugriffs Schlüsseln enthält. Die Schlüssel werden in einer Ressourcen Datei gespeichert, die nicht angezeigt wird. Ihre Werte werden jedoch in den auskommentierten `checkBox.Text` Zeilen angezeigt. Das Verhalten doppelter Acceleratoren kann durch Austauschen der `checkBox.Text` Zeilen mit ihren auskommentierten Entsprechungen überprüft werden. In diesem Fall wird in diesem Beispiel jedoch keine Warnung aus der Regel generiert.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Resources.ResourceManager?displayProperty=fullName> von [Ressourcen in Desktop-Apps](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)

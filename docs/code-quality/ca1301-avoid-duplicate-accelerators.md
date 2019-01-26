---
title: 'CA1301: Doppelte Zugriffstasten vermeiden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04a6c105f2452392af5c7246508232df18385b5e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018383"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Doppelte Zugriffstasten vermeiden.

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ erweitert <xref:System.Windows.Forms.Control?displayProperty=fullName> und enthält zwei oder mehr Steuerelemente der obersten Ebene, die gleichen Zugriffstasten verfügen, die in einer Ressourcendatei gespeichert werden.

## <a name="rule-description"></a>Regelbeschreibung

Eine Zugriffstaste, auch bekannt als Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement mit dem **Alt** Schlüssel. Wenn mehrere Steuerelemente über den gleichen Zugriffsschlüssel haben, ist das Verhalten des Zugriffsschlüssels nicht klar definiert. Der Benutzer möglicherweise nicht auf das gewünschte Steuerelement mit dem Zugriffsschlüssel zugreifen, und aktiviert ein Steuerelement als diejenige, die vorgesehen ist.

Die aktuelle Implementierung von dieser Regel werden, Menüelemente ignoriert. Menüelemente im gleichen Untermenü sollten jedoch nicht identischen Zugriffsschlüssel haben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Definieren Sie eindeutige Zugriffstasten für alle Steuerelemente, um einen Verstoß gegen diese Regel zu beheben.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein minimale Formular, das zwei Steuerelemente enthält, die über identische Zugriffsschlüssel verfügen. Der Schlüssel werden in einer Ressourcendatei gespeichert, der nicht angezeigt wird. Allerdings erscheinen ihre Werte in den auskommentierten out `checkBox.Text` Zeilen. Das Verhalten der doppelte Zugriffstasten untersucht werden kann, durch den Austausch von der `checkBox.Text` Zeilen mit den jeweiligen Entsprechungen auskommentierten. Allerdings wird in diesem Fall im Beispiel wird keine Warnung aus der Regel generiert.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index)
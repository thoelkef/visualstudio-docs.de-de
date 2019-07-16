---
title: 'CA1301: Doppelte Zugriffstasten vermeiden | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a2e992cfb648b9b7f84032abab2f96d3f7cb410d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686853"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Doppelte Zugriffstasten vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ erweitert <xref:System.Windows.Forms.Control?displayProperty=fullName> und enthält zwei oder mehr Steuerelemente der obersten Ebene, die gleichen Zugriffstasten verfügen, die in einer Ressourcendatei gespeichert werden.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement unter Verwendung der ALT-TASTE. Wenn mehrere Steuerelemente über doppelte Zugriffstasten verfügen, ist das Verhalten der Zugriffstaste nicht stringent. Der Benutzer möglicherweise nicht auf das gewünschte Steuerelement mit dem Zugriffsschlüssel zugreifen, und aktiviert ein Steuerelement als diejenige, die vorgesehen ist.

 Die aktuelle Implementierung von dieser Regel werden, Menüelemente ignoriert. Menüelemente im gleichen Untermenü sollten jedoch nicht identischen Zugriffsschlüssel haben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Definieren Sie eindeutige Zugriffstasten für alle Steuerelemente, um einen Verstoß gegen diese Regel zu beheben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein minimale Formular, das zwei Steuerelemente enthält, die über identische Zugriffsschlüssel verfügen. Die Schlüssel werden in einer Ressourcendatei gespeichert, der nicht angezeigt wird; Allerdings erscheinen ihre Werte in den auskommentierten out `checkBox.Text` Zeilen. Das Verhalten der doppelte Zugriffstasten untersucht werden kann, durch den Austausch von der `checkBox.Text` Zeilen mit den jeweiligen Entsprechungen auskommentierten. Allerdings wird in diesem Fall im Beispiel wird keine Warnung aus der Regel generiert.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Ressourcen in Desktop-Apps](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)

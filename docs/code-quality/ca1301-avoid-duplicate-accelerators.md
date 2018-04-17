---
title: 'CA1301: Doppelte Zugriffstasten vermeiden | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b9e2855827fb0befe69dafe08981b10a12d0700
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Doppelte Zugriffstasten vermeiden
|||  
|-|-|  
|TypeName|AvoidDuplicateAccelerators|  
|CheckId|CA1301|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Typ erweitert <xref:System.Windows.Forms.Control?displayProperty=fullName> und enthält zwei oder mehr Steuerelemente der obersten Ebene, die identische Zugriffstasten verfügen, die in einer Ressourcendatei gespeichert werden.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement unter Verwendung der ALT-TASTE. Wenn mehrere Steuerelemente über doppelte Zugriffstasten verfügen, ist das Verhalten der Zugriffstaste nicht stringent. Der Benutzer möglicherweise nicht auf das gewünschte Steuerelement mit der Zugriffstaste zugreifen und möglicherweise ein Steuerelement als diejenige, die vorgesehen ist aktiviert.  
  
 Die aktuelle Implementierung von dieser Regel werden die Menüelemente ignoriert. Menüelemente im gleichen Untermenü sollten jedoch nicht identischen Zugriffstasten haben.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, definieren Sie eindeutige Zugriffstasten für alle Steuerelemente.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein minimale Formular, das zwei Steuerelemente enthält, die identische Zugriffstasten verfügen. Die Schlüssel werden in einer Ressourcendatei gespeichert, die nicht angezeigt wird; jedoch erscheinen ihre Werte in der kommentierten out `checkBox.Text` Zeilen. Das Verhalten der doppelte Zugriffstasten untersucht werden kann, durch den Austausch der `checkBox.Text` Zeilen mit den jeweiligen Entsprechungen der als Kommentare formatiert. Allerdings wird in diesem Fall das Beispiel nicht generiert eine Warnung von der Regel.  
  
 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index)
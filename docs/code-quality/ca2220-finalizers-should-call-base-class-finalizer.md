---
title: 'CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 46427cffe64c6c81e0f262520a61c1b1ea01fff8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein Typ, der überschreibt <xref:System.Object.Finalize%2A?displayProperty=fullName> nicht aufgerufen, die <xref:System.Object.Finalize%2A> Methode in der Basisklasse.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies sicherzustellen, müssen die Typen aufrufen ihrer Basisklasse <xref:System.Object.Finalize%2A> Methode innerhalb ihrer eigenen <xref:System.Object.Finalize%2A> Methode. Der C#-Compiler fügt den Aufruf von den Basisklassen-Finalizer automatisch hinzu.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie den Basistyp <xref:System.Object.Finalize%2A> Methode aus Ihrer <xref:System.Object.Finalize%2A> Methode.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Einige Compiler, die die common Language Runtime abzielen fügen Sie einen Aufruf der Basistyp Finalizer in Microsoft intermediate Language (MSIL). Wenn eine Warnung dieser Regel gemeldet wird, Compiler kein Aufruf eingefügt, und Sie müssen diese für Ihren Code hinzufügen.  
  
## <a name="example"></a>Beispiel  
 Im folgende Visual Basic-Beispiel zeigt einen Typen `TypeB` ordnungsgemäß aufruft die <xref:System.Object.Finalize%2A> Methode in der Basisklasse.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)
---
title: 'CA2232: Markieren von Windows Forms-Einstiegspunkte mit STAThread markieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6dadac882d5a1b6bf96e4cb0f713979ff566116f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren
|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Eine Assembly verweist auf die <xref:System.Windows.Forms> Namespace und seine Einstiegspunkt ist nicht mit markiert die <xref:System.STAThreadAttribute?displayProperty=fullName> Attribut.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 <xref:System.STAThreadAttribute>Gibt an, dass die COM-Threadingmodell für die Anwendung Singlethread-Apartment ist. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig. Wenn das Attribut nicht vorhanden ist, verwendet die Anwendung das Multithread-Apartment-Modell, die nicht für Windows Forms unterstützt wird.  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Projekte, die das Anwendungsframework verwenden keine kennzeichnen die **Main** Methode mit STAThread markieren. Die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Compiler geschieht dies automatisch.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen die <xref:System.STAThreadAttribute> -Attribut auf den Einstiegspunkt. Wenn die <xref:System.MTAThreadAttribute?displayProperty=fullName> -Attribut vorhanden ist, entfernen Sie sie.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, sofern Sie für .NET Compact Framework für das Entwickeln der <xref:System.STAThreadAttribute> -Attribut ist nicht erforderlich und wird nicht unterstützt.  
  
## <a name="example"></a>Beispiel  
 Die folgenden Beispiele veranschaulichen die richtige Verwendung von <xref:System.STAThreadAttribute>.  
  
 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]
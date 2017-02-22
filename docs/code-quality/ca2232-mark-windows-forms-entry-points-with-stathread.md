---
title: "CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Assembly verweist auf den <xref:System.Windows.Forms>\-Namespace, und ihr Einstiegspunkt wird nicht mit dem <xref:System.STAThreadAttribute?displayProperty=fullName>\-Attribut markiert.  
  
## Regelbeschreibung  
 <xref:System.STAThreadAttribute> gibt an, dass das COM\-Threadingmodell für die Anwendung Singlethread\-Apartment ist.  Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows\-Komponenten eventuell nicht richtig.  Wenn das Attribut nicht vorhanden ist, verwendet die Anwendung das Multithreaded\-Apartmentmodell, das von Windows Forms nicht unterstützt wird.  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Projekte, die das Anwendungsframework verwenden, müssen die **Main**\-Methode nicht mit STAThread markieren.  Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler führt die Markierung automatisch aus.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie dem Einstiegspunkt das <xref:System.STAThreadAttribute>\-Attribut hinzu.  Wenn das <xref:System.MTAThreadAttribute?displayProperty=fullName>\-Attribut vorhanden ist, entfernen Sie es.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn Sie eine Anwendung für .NET Compact Framework entwickeln. In diesem Fall ist das <xref:System.STAThreadAttribute>\-Attribut überflüssig und wird nicht unterstützt.  
  
## Beispiel  
 In den folgenden Beispielen wird die richtige Verwendung von <xref:System.STAThreadAttribute> veranschaulicht.  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]
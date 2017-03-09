---
title: "CA1301: Doppelte Zugriffstasten vermeiden | Microsoft Docs"
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
  - "CA1301"
  - "AvoidDuplicateAccelerators"
helpviewer_keywords: 
  - "CA1301"
  - "AvoidDuplicateAccelerators"
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1301: Doppelte Zugriffstasten vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidDuplicateAccelerators|  
|CheckId|CA1301|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ erweitert <xref:System.Windows.Forms.Control?displayProperty=fullName> und enthält mindestens zwei Steuerelemente der obersten Ebene mit identischen Zugriffstasten, die in einer Ressourcendatei gespeichert sind.  
  
## Regelbeschreibung  
 Eine Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement unter Verwendung der ALT\-TASTE.  Wenn mehrere Steuerelemente über doppelte Zugriffstasten verfügen, ist das Verhalten der Zugriffstaste nicht stringent.  Der Benutzer kann unter Umständen mithilfe der Zugriffstaste nicht auf das gewünschte Steuerelement zugreifen, und möglicherweise wird nicht das gewünschte Steuerelement aktiviert.  
  
 Bei der aktuellen Implementierung dieser Regel werden Menüelemente ignoriert.  Menüelemente im gleichen Untermenü sollten jedoch nicht die gleichen Zugriffstasten haben.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, definieren Sie eindeutige Zugriffstasten für alle Steuerelemente.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird ein minimales Formular dargestellt, das zwei Steuerelemente mit gleichen Zugriffstasten enthält.  Die Tasten sind in einer Ressourcendatei gespeichert, die nicht dargestellt ist. Die Werte dieser Tasten sind jedoch in den auskommentierten `checkBox.Text`\-Zeilen enthalten.  Das Verhalten doppelter Zugriffstasten kann überprüft werden, indem die `checkBox.Text`\-Zeilen durch ihre auskommentierten Gegenstücke ausgetauscht werden.  In diesem Fall wird im Beispiel jedoch keine Warnung aus der Regel generiert.  
  
 [!code-cs[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]  
  
## Siehe auch  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Ressourcen in Desktop\-Apps](../Topic/Resources%20in%20Desktop%20Apps.md)
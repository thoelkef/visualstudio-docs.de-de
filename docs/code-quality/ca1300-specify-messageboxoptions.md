---
title: "CA1300: MessageBoxOptions angeben | Microsoft Docs"
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
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300: MessageBoxOptions angeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode ruft eine Überladung der <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>\-Methode auf, die kein <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>\-Argument annimmt.  
  
## Regelbeschreibung  
 Damit in Kulturen, in denen von rechts nach links gelesen wird, ein Meldungsfeld ordnungsgemäß angezeigt wird, müssen der <xref:System.Windows.Forms.MessageBoxOptions>\-Member und der <xref:System.Windows.Forms.MessageBoxOptions>\-Member der <xref:System.Windows.Forms.MessageBoxOptions>\-Enumeration an die <xref:System.Windows.Forms.MessageBox.Show%2A>\-Methode übergeben werden.  Überprüfen Sie die <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>\-Eigenschaft des Containersteuerelements, um festzustellen, ob eine Rechts\-nach\-Links\-Lesefolge verwendet werden soll.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie eine Überladung der <xref:System.Windows.Forms.MessageBox.Show%2A>\-Methode auf, die ein <xref:System.Windows.Forms.MessageBoxOptions>\-Argument annimmt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Codebibliothek nicht für eine Kultur lokalisiert wird, in der von rechts nach links gelesen wird.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Methode, die ein Meldungsfeld mit Optionen anzeigt, die der Lesefolge der Kultur entsprechen.  Zur Erstellung des Beispielcodes wird eine Ressourcendatei \(nicht dargestellt\) benötigt.  Folgen Sie dem Kommentar im Beispiel, um das Beispiel ohne eine Ressourcendatei zu erstellen und das Rechts\-nach\-Links\-Feature zu testen.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## Siehe auch  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Ressourcen in Desktop\-Apps](../Topic/Resources%20in%20Desktop%20Apps.md)
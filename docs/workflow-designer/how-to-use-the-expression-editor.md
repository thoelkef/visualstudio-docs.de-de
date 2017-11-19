---
title: 'Vorgehensweise: Verwenden Sie den Ausdrucks-Editor | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: "13"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: b7deb3daed85c0c15d299052642abcb732ff12c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-use-the-expression-editor"></a>Vorgehensweise: Verwenden des Ausdrucks-Editors
Der Ausdrucks-Editor ist ein [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]-Steuerelement, das in vielen Workflowaktivitäten zum Eingeben und Auswerten von Ausdrücken verwendet wird. Der Ausdrucks-Editor stellt vollständige IDE-Bearbeitungsumgebung bereit, einschließlich IntelliSense, Einfärbung, ParamInfo, Fehlerschnörkel und weitere Funktionen. Der Compiler überprüft den Ausdruck, nachdem er eingegeben wurde. Wenn der Ausdruck ungültig ist, wird ein Fehlersymbol angezeigt. Der Editor kann auch geöffnet werden, als ein **Ausdrucks-Editor** (Dialogfeld).  
  
 Ausdrücke sind an Argumente oder Eigenschaften gebundene literale Werte oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Code. Sie enthalten Wertelemente, die (z. B. Variablen, Konstanten, Literale, Eigenschaften), die mit Vorgängen kombiniert werden, um einen neuen Wert zu ergeben. Ausdrücke werden mit VB.NET-Syntax geschrieben, auch wenn sie in einem in C# geschriebenen Programm verwendet werden. Dies bedeutet, dass Großschreibung spielt keine Rolle, Vergleich erfolgt über ein einzelnes Gleichheitszeichen ("=") anstelle von ("==") sind die booleschen Operatoren die Wörter "und" und "or" statt der Symbole "& &" und "&#124; &#124;", und **nichts**  anstelle von **null**. Weitere Informationen zu Ausdrücken und Operatoren in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] und einige Beispiele finden Sie unter [Operatoren und Ausdrücke in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).  
  
 Die **Ausdrucks-Editor** verhält sich wie folgt:  
  
-   Wenn der Ausdrucks-Editor nicht im Fokus ist, sieht er wie ein reguläres TextBlock-Steuerelement aus.  
  
-   Sobald der Fokus auf dem Ausdrucks-Editor ist, sieht er wie das Ausdrucks-Editor-Steuerelement aus und verhält sich wie dieses. Nachdem er den Fokus verloren hat, das er sieht wieder wie ein reguläres TextBlock-Steuerelement aus.  
  
-   Wenn Sie in einem neu gehosteten Workflow-Designer den Fokus auf den Ausdrucks-Editor legen, dann verhält er sich wie ein Textfeld. Wenn der Ausdrucks-Editor im neu gehosteten Workflow-Designer den Fokus verliert, sieht er wieder wie ein regulärer TextBlock aus.  
  
> [!NOTE]
>  Für den Ausdrucks-Editor ist IntelliSense nur innerhalb von [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] verfügbar. Sowohl in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] als auch den neu gehosteten Szenarien überprüft der Compiler den Ausdruck, nachdem er eingegeben wurde, und der Ausdrucks-Editor zeigt ein Fehlersymbol an, wenn der Ausdruck ungültig ist.  
  
### <a name="using-the-expression-editor"></a>Verwenden des Ausdrucks Editors  
  
1.  Öffnen Sie in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ein neues oder vorhandenes Workflowprojekt aus.  
  
2.  Fügen Sie dem Workflow z. B. die <xref:System.Activities.Statements.Assign>-Aktivität hinzu.  
  
    > [!NOTE]
    >  Mehrere Workflowaktivitäten verfügen über Ausdrucks-Editoren. Ausdrucks-TextBlock-Steuerelemente werden auch im Variablen-Designer, Argument-Designer und dem dynamischen Argument-Designer angezeigt. Die <xref:System.Activities.Statements.Assign>-Aktivität wird als Beispiel verwendet.  
  
3.  Klicken Sie im Aktivitätsdesigner für die <xref:System.Activities.Statements.Assign>-Aktivität auf den linken Ausdrucks-Editor.  
  
     Die grauen Wasserzeichen Zeichenfolgen  **\<um >** und  **\<VB-Ausdruck eingeben >** werden standardmäßig Textzeichenfolgen für Ausdrucks-Editoren in der <xref:System.Activities.Statements.Assign> Aktivität.  
  
4.  Geben Sie einen Ausdruck ein. Wenn Sie eine Zeichenfolge eingeben, setzen Sie diese unbedingt in Anführungszeichen. Wenn Sie das Ausdrucksargument an eine Variable zu binden, lassen Sie die Anführungszeichen weg.  
  
     Danach wählen Sie einen Bereich außerhalb des Ausdrucks-Editors aus, um den Fokus zu einem anderen Teil des Designers zu verlagern. Dies bewirkt, dass der Compiler den Ausdruck wie zuvor beschrieben überprüft.  
  
     Eine andere Möglichkeit, einen Ausdruck einzugeben oder zu bearbeiten, besteht darin, auf die Auslassungspunkte neben einem Eigenschaftennamen im Eigenschaftenraster zu klicken. Dies öffnet die **Ausdrucks-Editor** unter (Dialogfeld).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>
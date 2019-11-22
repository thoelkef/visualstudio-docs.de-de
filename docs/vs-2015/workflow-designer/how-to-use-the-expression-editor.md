---
title: 'How to: Use the Expression Editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d40cefc3dd47f7f4ad7e8255d8bdc06bc5f1651
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300941"
---
# <a name="how-to-use-the-expression-editor"></a>Vorgehensweise: Verwenden des Ausdrucks-Editors
Der Ausdrucks-Editor ist ein [!INCLUDE[wfd1](../includes/wfd1-md.md)]-Steuerelement, das in vielen Workflowaktivitäten zum Eingeben und Auswerten von Ausdrücken verwendet wird. Der Ausdrucks-Editor stellt vollständige IDE-Bearbeitungsumgebung bereit, einschließlich IntelliSense, Einfärbung, ParamInfo, Fehlerschnörkel und weitere Funktionen. Der Compiler überprüft den Ausdruck, nachdem er eingegeben wurde. Wenn der Ausdruck ungültig ist, wird ein Fehlersymbol angezeigt. The editor can also be opened as an **Expression Editor** dialog box.

 Ausdrücke sind an Argumente oder Eigenschaften gebundene literale Werte oder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Code. Sie enthalten Wertelemente, die (z. B. Variablen, Konstanten, Literale, Eigenschaften), die mit Vorgängen kombiniert werden, um einen neuen Wert zu ergeben. Ausdrücke werden mit VB.NET-Syntax geschrieben, auch wenn sie in einem in C# geschriebenen Programm verwendet werden. This means capitalization does not matter, comparison is performed using a single equals (“=”) sign instead of (“==”), the Boolean operators are the words "and" and "or" instead of the symbols "&&" and "&#124;&#124;", and **Nothing** is used instead of **null**. For more information on expressions and operators in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] and for some samples, see [Operators and Expressions in Visual Basic](https://go.microsoft.com/fwlink/?LinkId=186818).

 The **Expression Editor** behaves as follows:

- Wenn der Ausdrucks-Editor nicht im Fokus ist, sieht er wie ein reguläres TextBlock-Steuerelement aus.

- Sobald der Fokus auf dem Ausdrucks-Editor ist, sieht er wie das Ausdrucks-Editor-Steuerelement aus und verhält sich wie dieses. Nachdem er den Fokus verloren hat, das er sieht wieder wie ein reguläres TextBlock-Steuerelement aus.

- Wenn Sie in einem neu gehosteten Workflow-Designer den Fokus auf den Ausdrucks-Editor legen, dann verhält er sich wie ein Textfeld. Wenn der Ausdrucks-Editor im neu gehosteten Workflow-Designer den Fokus verliert, sieht er wieder wie ein regulärer TextBlock aus.

> [!NOTE]
> Für den Ausdrucks-Editor ist IntelliSense nur innerhalb von [!INCLUDE[vs2010](../includes/vs2010-md.md)] verfügbar. Sowohl in [!INCLUDE[vs2010](../includes/vs2010-md.md)] als auch den neu gehosteten Szenarien überprüft der Compiler den Ausdruck, nachdem er eingegeben wurde, und der Ausdrucks-Editor zeigt ein Fehlersymbol an, wenn der Ausdruck ungültig ist.

### <a name="using-the-expression-editor"></a>Verwenden des Ausdrucks Editors

1. Öffnen Sie in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ein neues oder vorhandenes Workflowprojekt aus.

2. Fügen Sie dem Workflow z. B. die <xref:System.Activities.Statements.Assign>-Aktivität hinzu.

    > [!NOTE]
    > Mehrere Workflowaktivitäten verfügen über Ausdrucks-Editoren. Ausdrucks-TextBlock-Steuerelemente werden auch im Variablen-Designer, Argument-Designer und dem dynamischen Argument-Designer angezeigt. Die <xref:System.Activities.Statements.Assign>-Aktivität wird als Beispiel verwendet.

3. Klicken Sie im Aktivitätsdesigner für die <xref:System.Activities.Statements.Assign>-Aktivität auf den linken Ausdrucks-Editor.

     The grey watermark strings **\<To>** and **\<Enter a VB Expression>** are the default text strings for expression editors in the <xref:System.Activities.Statements.Assign> activity.

4. Geben Sie einen Ausdruck ein. Wenn Sie eine Zeichenfolge eingeben, setzen Sie diese unbedingt in Anführungszeichen. Wenn Sie das Ausdrucksargument an eine Variable zu binden, lassen Sie die Anführungszeichen weg.

     Danach wählen Sie einen Bereich außerhalb des Ausdrucks-Editors aus, um den Fokus zu einem anderen Teil des Designers zu verlagern. Dies bewirkt, dass der Compiler den Ausdruck wie zuvor beschrieben überprüft.

     Eine andere Möglichkeit, einen Ausdruck einzugeben oder zu bearbeiten, besteht darin, auf die Auslassungspunkte neben einem Eigenschaftennamen im Eigenschaftenraster zu klicken. This will open the **Expression Editor** as dialog box.

## <a name="see-also"></a>Siehe auch
 <xref:System.Activities.Presentation.View.ExpressionTextBox>
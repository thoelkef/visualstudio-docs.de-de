---
title: 'Workflow-Designer - Vorgehensweise: Verwenden Sie den Ausdrucks-Editor'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e14a967b9721973d8d545e10f58cab3c68b8e15
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976503"
---
# <a name="how-to-use-the-expression-editor"></a>Vorgehensweise: Verwenden des Ausdrucks-Editors

Der Ausdrucks-Editor ist ein Windows-Workflow-Designer-Steuerelement, das in vielen Workflowaktivitäten als Mittel zum eingeben und Auswerten von Ausdrücken verwendet wird. Der Ausdrucks-Editor stellt vollständige IDE-Bearbeitungsumgebung bereit, einschließlich IntelliSense, Einfärbung, ParamInfo, Fehlerschnörkel und weitere Funktionen. Der Compiler überprüft den Ausdruck, nachdem er eingegeben wurde. Wenn der Ausdruck ungültig ist, wird ein Fehlersymbol angezeigt. Der Editor kann auch geöffnet werden, als ein **Ausdrucks-Editor** (Dialogfeld).

 Ausdrücke sind an Argumente oder Eigenschaften gebundene literale Werte oder Visual Basic-Code. Sie enthalten Wertelemente, die (z. B. Variablen, Konstanten, Literale, Eigenschaften), die mit Vorgängen kombiniert werden, um einen neuen Wert zu ergeben. Ausdrücke werden mit VB.NET-Syntax geschrieben, auch wenn sie in einem in C# geschriebenen Programm verwendet werden. Dies bedeutet, dass Großschreibung spielt keine Rolle, Vergleich erfolgt über ein einzelnes Gleichheitszeichen ("=") anstelle von ("==") sind die booleschen Operatoren die Wörter "und" und "or" statt der Symbole "& &" und "&#124;&#124;", und **nichts**  anstelle von **null**. Weitere Informationen zu Ausdrücken und Operatoren in Visual Basic und einige Beispiele finden Sie in [Operatoren und Ausdrücke in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).

 Die **Ausdrucks-Editor** verhält sich wie folgt:

-   Wenn der Ausdrucks-Editor nicht im Fokus ist, sieht er wie ein reguläres TextBlock-Steuerelement aus.

-   Sobald der Fokus auf dem Ausdrucks-Editor ist, sieht er wie das Ausdrucks-Editor-Steuerelement aus und verhält sich wie dieses. Nachdem er den Fokus verloren hat, das er sieht wieder wie ein reguläres TextBlock-Steuerelement aus.

-   Wenn Sie in einem neu gehosteten Workflow-Designer den Fokus auf den Ausdrucks-Editor legen, dann verhält er sich wie ein Textfeld. Wenn der Ausdrucks-Editor im neu gehosteten Workflow-Designer den Fokus verliert, sieht er wieder wie ein regulärer TextBlock aus.

> [!NOTE]
> IntelliSense für den Ausdrucks-Editor ist nur innerhalb von Visual Studio 2010 verfügbar. In Visual Studio 2010 und den neu gehosteten Szenarien überprüft der Compiler den Ausdruck, nachdem eingegeben wird und der Ausdrucks-Editor wird ein Fehlersymbol angezeigt, wenn der Ausdruck ungültig ist.

## <a name="use-the-expression-editor"></a>Verwenden Sie den Ausdrucks-editor

1.  Öffnen Sie in Visual Studio 2010 ein neues oder vorhandenes Workflowprojekt aus.

2.  Fügen Sie dem Workflow z. B. die <xref:System.Activities.Statements.Assign>-Aktivität hinzu.

    > [!NOTE]
    > Mehrere Workflowaktivitäten verfügen über Ausdrucks-Editoren. Ausdrucks-TextBlock-Steuerelemente werden auch im Variablen-Designer, Argument-Designer und dem dynamischen Argument-Designer angezeigt. Die <xref:System.Activities.Statements.Assign>-Aktivität wird als Beispiel verwendet.

3.  Klicken Sie im Aktivitätsdesigner für die <xref:System.Activities.Statements.Assign>-Aktivität auf den linken Ausdrucks-Editor.

     Die grauen Wasserzeichen Zeichenfolgen  **\<um >** und  **\<VB-Ausdruck eingeben >** werden standardmäßig Textzeichenfolgen für Ausdrucks-Editoren in der <xref:System.Activities.Statements.Assign> Aktivität.

4.  Geben Sie einen Ausdruck ein. Wenn Sie eine Zeichenfolge eingeben, setzen Sie diese unbedingt in Anführungszeichen. Wenn Sie das Ausdrucksargument an eine Variable zu binden, lassen Sie die Anführungszeichen weg.

     Danach wählen Sie einen Bereich außerhalb des Ausdrucks-Editors aus, um den Fokus zu einem anderen Teil des Designers zu verlagern. Dies bewirkt, dass der Compiler den Ausdruck wie zuvor beschrieben überprüft.

     Eine andere Möglichkeit, einen Ausdruck einzugeben oder zu bearbeiten, besteht darin, auf die Auslassungspunkte neben einem Eigenschaftennamen im Eigenschaftenraster zu klicken. Dies öffnet die **Ausdrucks-Editor** unter (Dialogfeld).

## <a name="see-also"></a>Siehe auch

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
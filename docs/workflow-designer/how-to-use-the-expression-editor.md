---
title: 'Workflow-Designer – Vorgehensweise: Verwenden des Ausdrucks Editors'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fee9738cfce003ef19d311856304d87f6a4b2f15
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918909"
---
# <a name="how-to-use-the-expression-editor"></a>Vorgehensweise: Verwenden des Ausdrucks Editors

Der Ausdrucks-Editor ist ein Workflow-Designer-Steuerelement, das in vielen Workflowaktivitäten zum eingeben und Auswerten von Ausdrücken verwendet wird. Der Ausdrucks-Editor stellt vollständige IDE-Bearbeitungsfunktionen Oberfläche, einschließlich IntelliSense, Einfärbung, ParamInfo, Fehlerschnörkel, andere Features. Der Compiler überprüft den Ausdruck aus, nachdem er eingegeben wurde. Wenn der Ausdruck ungültig ist, wird ein Fehlersymbol angezeigt. Der Editor kann auch geöffnet werden, als ein **Ausdrucks-Editor** Dialogfeld.

Ausdrücke sind an Argumente oder Eigenschaften gebundene literale Werte oder Visual Basic-Code. Sie enthalten Wertelemente (z. B. Variablen, Konstanten, Literale, Eigenschaften), die mit Vorgängen um einen neuen Wert zu erhalten, kombiniert werden. Ausdrücke werden mit VB.NET-Syntax geschrieben, auch wenn sie in einem in C# geschriebenen Programm verwendet werden. Dies bedeutet, dass Großschreibung spielt keine Rolle, Vergleich wird ausgeführt, die mit einem einzelnen entspricht signieren ("=" anstelle von "==") sind die booleschen Operatoren die Wörter "and" und "or" statt der Symbole "& &" und "||", und **"Nothing"** wird verwendet, anstelle von **null**. Weitere Informationen zu Ausdrücken und Operatoren in Visual Basic und einige Beispiele finden Sie [Operatoren und Ausdrücke in Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

Die **Ausdrucks-Editor** verhält sich wie folgt:

- Wenn der Ausdrucks-Editor nicht im Fokus ist, sieht er wie ein reguläres TextBlock-Steuerelement aus.

- Sobald der Fokus auf dem Ausdrucks-Editor ist, sieht er wie das Ausdrucks-Editor-Steuerelement aus und verhält sich wie dieses. Nachdem sie den Fokus verliert, sieht der Ausdrucks-Editor ein reguläres TextBlock-Steuerelement erneut aus.

- Wenn Sie in einem neu gehosteten Workflow-Designer den Fokus auf den Ausdrucks-Editor legen, dann verhält er sich wie ein Textfeld. Wenn der Ausdrucks-Editor im neu gehosteten Workflow-Designer den Fokus verliert, sieht er wieder wie ein regulärer TextBlock aus.

> [!NOTE]
> IntelliSense für den Ausdrucks-Editor ist nur in Visual Studio verfügbar. In der Visual Studio und den neu gehosteten Szenarien überprüft der Compiler den Ausdruck aus, nachdem eingegeben wird und der Ausdrucks-Editor zeigt ein Fehlersymbol an, wenn der Ausdruck ungültig ist.

## <a name="use-the-expression-editor"></a>Verwenden des Ausdrucks-Editors

1.  Öffnen Sie in Visual Studio ein neues oder vorhandenes Workflowprojekt aus.

2.  Fügen Sie dem Workflow z. B. die <xref:System.Activities.Statements.Assign>-Aktivität hinzu.

    > [!NOTE]
    > Mehrere Workflowaktivitäten verfügen über Ausdrucks-Editoren. Ausdrucks-TextBlock-Steuerelemente werden auch im Variablen-Designer, Argument-Designer und dem dynamischen Argument-Designer angezeigt. Die <xref:System.Activities.Statements.Assign>-Aktivität wird als Beispiel verwendet.

3.  Klicken Sie im Aktivitätsdesigner für die <xref:System.Activities.Statements.Assign>-Aktivität auf den linken Ausdrucks-Editor.

     Die grauen Wasserzeichen Zeichenfolgen  **\<auf >** und  **\<VB-Ausdruck eingeben >** sind die standardtextzeichenfolgen für Ausdrucks-Editoren in der <xref:System.Activities.Statements.Assign> Aktivität.

4.  Geben Sie einen Ausdruck ein. Wenn Sie eine Zeichenfolge eingeben, setzen Sie diese unbedingt in Anführungszeichen. Wenn Sie das Ausdrucksargument an eine Variable zu binden, lassen Sie die Anführungszeichen weg.

     Wenn Sie fertig sind, wählen Sie eine Region oder einen Bereich außerhalb der Ausdrucks-Editor, um den Fokus auf einen anderen Teil des Designers zu verlagern. Verschieben des Fokus bewirkt, dass der Compiler den Ausdruck zu überprüfen, wie zuvor beschrieben.

     Eine alternative Methode zum eingeben oder Bearbeiten eines Ausdrucks ist mit den Auslassungspunkten neben dem Eigenschaftennamen im Eigenschaftenraster auf. Öffnen Sie auf die Auslassungspunkte die **Ausdrucks-Editor** als Dialogfeld.

## <a name="see-also"></a>Siehe auch

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
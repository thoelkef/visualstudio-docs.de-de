---
title: 'Workflow-Designer – Vorgehensweise: definieren und Verarbeiten von aktivitätsdelegaten'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 32546f551972cf97779e0828d8c47c9c892d39bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916357"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer

.NET Framework 4.5 enthält einen Out-of-Box-Designer für die <xref:System.Activities.Statements.InvokeDelegate> Aktivität. Der Designer kann verwendet werden, um der Aktivität Delegate zuzuweisen, die von <xref:System.Activities.ActivityDelegate>, z. B. <xref:System.Activities.ActivityAction> oder <xref:System.Activities.ActivityFunc%601>, abgeleitet werden.

## <a name="define-an-activity-delegate"></a>Definieren eines Aktivitätsdelegaten

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt**.

2. In der **neues Projekt** wählen Sie im Dialogfeld die **Workflow** Kategorie auf der linken Seite, und wählen Sie dann die **Konsolenanwendung für Workflows** Projektvorlage. Nennen Sie das Projekt (falls gewünscht), und klicken Sie auf **Ok**.

   > [!NOTE]
   > Wenn Sie nicht sehen die **Workflow** Kategorie, der ersten Installation der **Windows Workflow Foundation** Komponente von Visual Studio 2017. Ausführliche Anweisungen finden Sie unter [Installieren von Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** , und wählen Sie **hinzufügen** > **neues Element**. Wählen Sie die **Workflow** Kategorie, und wählen Sie dann die **Aktivität** Elementvorlage. Nennen Sie die neue Aktivität **MyForEach.xaml** und wählen Sie dann **OK**.

   Die Aktivität, die im Workflow-Designer wird geöffnet.

4. Klicken Sie im Workflow-Designer auf die **Argumente** Registerkarte.

5. Klicken Sie auf **Argument erstellen**. Nennen Sie das neue Argument **Elemente**.

6. In der **Argumenttyp** Spalte **Array von [T]**.

7. Wählen Sie im Typbrowser **Objekt** und wählen Sie dann **OK**.

8. Klicken Sie auf **Argument erstellen** erneut aus. Nennen Sie das neue Argument **Text**. In der **Richtung** Spalte für das neue Argument die Option **Eigenschaft**.

9. Wählen Sie in der Spalte Argumenttyp **nach Typen suchen**

10. Geben Sie im Typbrowser **ActivityAction** in die **Typnamen** Feld. Wählen Sie **ActivityAction\<T >** in der Strukturansicht angezeigt. Wählen Sie **Objekt** in der eingeblendeten-Typ zuzuweisen **ActivityAction\<Objekt >** an das Argument.

11. Ziehen Sie eine <xref:System.Activities.Statements.While> Aktivität aus der **Ablaufsteuerung** Abschnitt der Toolbox auf die Designeroberfläche.

12. Wählen Sie die <xref:System.Activities.Statements.While> -Aktivität, und wählen die **Variablen** Registerkarte.

13. Wählen Sie **erstellen Variable**. Benennen Sie die neue Variable **Index**.

14. In der **Variablentyp** Spalte **Int32**. Lassen Sie die **Bereich** als **während**, und die **Standard** Spalte leer.

15. Legen Sie die **Bedingung** Eigenschaft der <xref:System.Activities.Statements.While> Aktivität **Index < Items.Length;**.

16. Ziehen Sie ein <xref:System.Activities.Statements.InvokeDelegate> Aktivität aus der **primitive** Abschnitt der Toolbox auf die **Text** von der <xref:System.Activities.Statements.While> Aktivität.

17. Wählen Sie **Text** in der Dropdown-Liste von Delegaten.

18. In der **Eigenschaften** Raster für die <xref:System.Activities.Statements.InvokeDelegate> -Aktivität, klicken Sie auf die **...**  Schaltfläche der **Delegatargumente** Eigenschaft.

19. In der **Wert** Spalte des Arguments mit dem Namen **Argument**, geben Sie **Items [Index]**. Klicken Sie auf **Ok** schließen die **DelegateArguments** Dialogfeld.

20. Ziehen Sie eine <xref:System.Activities.Statements.Assign>-Aktivität auf die horizontale Linie unterhalb der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Die <xref:System.Activities.Statements.Assign> -Aktivität wird erstellt, und ein <xref:System.Activities.Statements.Sequence> Aktivität wird automatisch erstellt, um die beiden Aktivitäten im der **Text** Teil der **MyForEach** Aktivität. Die Sequenz wird benötigt, da die **Text** Abschnitt kann nur eine einzige Aktivität enthalten. Automatisch beim Erstellen eines neuen <xref:System.Activities.Statements.Sequence> Aktivität ist ein neues Feature von .NET Framework 4.5.

21. Festlegen der **zu** Eigenschaft der <xref:System.Activities.Statements.Assign> Aktivität **Index**. Festlegen der **Wert** Eigenschaft der **zuweisen** Aktivität **Index + 1**.

    Die benutzerdefinierte **MyForEach** Aktivität Ruft eine beliebige Aktivität einmal für jeden Wert, der übergeben werden, über die **Elemente** Sammlung mit den Werten in der Auflistung als Eingaben für die Aktivität.

## <a name="use-the-custom-activity-in-a-workflow"></a>Verwenden der benutzerdefinierten Aktivität in einem Workflow

1.  Erstellen Sie das Projekt durch Drücken von **STRG**+**UMSCHALT**+**B**.

2.  In **Projektmappen-Explorer**öffnen **"Workflow1.xaml"** im Designer.

3.  Ziehen Sie eine **MyForEach** Aktivität aus der Toolbox auf die Designeroberfläche. Die Aktivität ist in einem Abschnitt der Toolbox mit dem gleichen Namen wie das Projekt.

4.  Legen Sie die **Elemente** Eigenschaft der **MyForEach** Aktivität **new Object [] {1, "Abc"}**.

5.  Ziehen Sie eine <xref:System.Activities.Statements.WriteLine> Aktivität aus der **primitive** Abschnitt der Toolbox auf die **Delegate: Body** Teil der **MyForEach** Aktivität.

6.  Legen Sie die **Text** Eigenschaft der <xref:System.Activities.Statements.WriteLine> Aktivität **Argument.ToString()**.

Wenn der Workflow ausgeführt wird, wird die Konsole die folgende Ausgabe:

**1**
**Abc**
---
title: 'Workflow-Designer - Vorgehensweise: definieren und Verarbeiten von aktivitätsdelegaten'
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
ms.openlocfilehash: 73bf61c845b0124a8350f61c161ded1cf0c80043
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer

.NET Framework 4.5 umfasst einen neuen Out-of-Box-Designer für die <xref:System.Activities.Statements.InvokeDelegate> Aktivität. Der Designer kann verwendet werden, um der Aktivität Delegate zuzuweisen, die von <xref:System.Activities.ActivityDelegate>, z. B. <xref:System.Activities.ActivityAction> oder <xref:System.Activities.ActivityFunc%601>, abgeleitet werden.

## <a name="define-an-activity-delegate"></a>Definieren eines Aktivitätsdelegaten

1.  Wählen Sie in Visual Studio **Datei**, **neu**, **Projekt**. Wählen Sie die **Workflow** Knoten auf der linken Seite und die **Workflowkonsolenanwendung** Vorlage auf der rechten Seite. Nennen Sie das Projekt (falls gewünscht), und klicken Sie auf **Ok**.

2.  Mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** , und wählen Sie **hinzufügen**, **neues Element...** . Wählen Sie die **Workflow** Knoten auf der linken Seite und die **Aktivität** Vorlage auf der rechten Seite. Benennen Sie die neue Aktivität **MyForEach.xaml** , und klicken Sie auf **Ok**. Die Aktivität wird im Workflow-Designer geöffnet.

3.  Klicken Sie im Workflow-Designer auf die **Argumente** Registerkarte.

4.  Klicken Sie auf **Argument erstellen**. Nennen Sie das neue Argument **Elemente**.

5.  In der **Argumenttyp** Spalte **Array von [T]**.

6.  Wählen Sie im Typbrowser **Objekt**. Click **Ok**.

7.  Klicken Sie auf **Argument erstellen** erneut aus. Nennen Sie das neue Argument **Text**. In der **Richtung** Spalte für das neue Argument die Option **Eigenschaft**.

8.  Wählen Sie in der Spalte Argumenttyp **nach Typen suchen...**

9. Geben Sie im Typbrowser **ActivityAction** in der **Typnamen** Feld. Wählen Sie **ActivityAction\<T >** in der Strukturansicht. Wählen Sie **Objekt** in der Dropdownliste aus, die angezeigt wird, weisen die **ActivityAction\<Objekt >** an das Argument.

10. Ziehen Sie eine <xref:System.Activities.Statements.While> Aktivität aus der **Control Flow** Abschnitt der Toolbox auf die Designeroberfläche.

11. Wählen Sie die <xref:System.Activities.Statements.While> Aktivität, und wählen die **Variablen** Registerkarte.

12. Wählen Sie **erstellen Variable**. Benennen Sie die neue Variable **Index**.

13. In der **Variablentyp** Spalte **Int32**. Lassen Sie die **Bereich** als **während**, und die **Standard** Spalte leer.

14. Festlegen der **Bedingung** Eigenschaft von der <xref:System.Activities.Statements.While> Aktivität **Index < Items.Length;**.

15. Ziehen Sie ein <xref:System.Activities.Statements.InvokeDelegate> Aktivität aus der **primitive** Abschnitt der Toolbox auf die **Text** von der <xref:System.Activities.Statements.While> Aktivität.

16. Wählen Sie **Text** in der Dropdownliste Delegaten.

17. In der **Eigenschaften** Raster für die <xref:System.Activities.Statements.InvokeDelegate> Aktivität, klicken Sie auf der **...**  Schaltfläche der **Delegatargumente** Eigenschaft.

18. In der **Wert** Spalte des Arguments mit dem Namen **Argument**, geben Sie **Items [Index]**. Klicken Sie auf **Ok** schließen die **DelegateArguments** Dialogfeld.

19. Ziehen Sie eine <xref:System.Activities.Statements.Assign>-Aktivität auf die horizontale Linie unterhalb der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Die <xref:System.Activities.Statements.Assign> Aktivität erstellt werden soll, und ein <xref:System.Activities.Statements.Sequence> Aktivität wird automatisch erstellt werden, um die beiden Aktivitäten im die **Text** Teil der **MyForEach** Aktivität. Die Sequenz wird benötigt, da die **Text** Abschnitt kann nur eine einzige Aktivität enthalten. Automatisch beim Erstellen eines neuen <xref:System.Activities.Statements.Sequence> Aktivität ist ein neues Feature von .NET Framework 4.5.

20. Festlegen der **zu** Eigenschaft von der <xref:System.Activities.Statements.Assign> Aktivität **Index**. Festlegen der **Wert** Eigenschaft von der **zuweisen** Aktivität **Index + 1**.

 Die benutzerdefinierte **MyForEach** -Aktivität ruft nun eine beliebige Aktivität einmal für jeden Wert übergeben werden, über die **Elemente** Auflistung mit den Werten in der Auflistung als Eingaben für die Aktivität definiert.

## <a name="use-the-custom-activity-in-a-workflow"></a>Verwenden der benutzerdefinierten Aktivität in einem Workflow

1.  Erstellen Sie das Projekt, indem Sie drücken **STRG + UMSCHALT + B**.

2.  In **Projektmappen-Explorer**öffnen **"Workflow1.xaml"** im Designer.

3.  Ziehen Sie eine **MyForEach** Aktivität aus der Toolbox auf die Designeroberfläche. Die Aktivität befindet sich in einem Abschnitt der Toolbox mit dem gleichen Namen wie das Projekt.

4.  Festlegen der **Elemente** Eigenschaft von der **MyForEach** Aktivität **new Object [] {1, "Abc"}**.

5.  Ziehen Sie eine <xref:System.Activities.Statements.WriteLine> Aktivität aus der **primitive** Abschnitt der Toolbox auf die **Delegate: Body** Teil der **MyForEach** Aktivität.

6.  Festlegen der **Text** Eigenschaft von der <xref:System.Activities.Statements.WriteLine> Aktivität **Argument.ToString()**.

Wenn der Workflow ausgeführt wird, zeigt die Konsole Folgendes:

**1**
**Abc**
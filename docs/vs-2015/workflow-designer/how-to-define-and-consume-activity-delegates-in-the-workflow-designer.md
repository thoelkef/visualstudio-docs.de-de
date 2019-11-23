---
title: 'Gewusst wie: definieren und Verarbeiten von Aktivitäts Delegaten im Workflow-Designer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603857"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer
[!INCLUDE[net_v45](../includes/net-v45-md.md)] enthält einen neuen Standard Designer für die <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Der Designer kann verwendet werden, um der Aktivität Delegate zuzuweisen, die von <xref:System.Activities.ActivityDelegate>, z. B. <xref:System.Activities.ActivityAction> oder <xref:System.Activities.ActivityFunc%601>, abgeleitet werden.

### <a name="define-an-activity-delegate"></a>Definieren eines Aktivitätsdelegaten

1. Wählen Sie in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]die Option **Datei**, **neu**und **Projekt**aus. Wählen Sie auf der linken Seite den Knoten **Workflow** und die Vorlage **Konsolenanwendung für Workflows** auf der rechten Seite aus. Benennen Sie das Projekt (falls gewünscht), und klicken Sie auf **OK**.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen**, **Neues Element...** aus. Wählen Sie auf der linken Seite den Knoten **Workflow** und die **Aktivitäts** Vorlage auf der rechten Seite aus. Nennen Sie die neue Aktivität **myforeach. XAML** , und klicken Sie auf **OK**. Die Aktivität wird im Workflow-Designer geöffnet.

3. Klicken Sie im Workflow-Designer auf die Registerkarte **Argumente** .

4. Klicken Sie auf **Argument erstellen**. Benennen Sie die neuen Argument **Elemente**.

5. Wählen Sie in der Spalte **Argumenttyp** die Option **Array von [T] aus**.

6. Wählen Sie im Typbrowser die Option **Objekt**aus. Klicken Sie auf **OK**.

7. Klicken Sie erneut auf **Argument erstellen** . Benennen Sie den neuen Argument **Text**. Wählen Sie in der Spalte **Richtung** für das neue Argument **Eigenschaft**aus.

8. Wählen Sie in der Spalte Argumenttyp die Option **nach Typen suchen... aus.**

9. Geben Sie im Typbrowser im Feld **Typname den Namen** **ActivityAction** ein. Wählen Sie in der Strukturansicht **ActivityAction\<t >** aus. Wählen Sie in der Dropdown Liste die Option **Objekt** aus, die den Typ **ActivityAction\<Objekt >** dem Argument zuweist.

10. Ziehen Sie eine <xref:System.Activities.Statements.While>-Aktivität aus dem Abschnitt **Ablauf Steuerung** der Toolbox auf die Designer Oberfläche.

11. Wählen Sie die <xref:System.Activities.Statements.While> Aktivität aus, und klicken Sie auf die Registerkarte **Variablen** .

12. Wählen Sie **Variable erstellen**aus. Benennen Sie den neuen Variablen **Index**.

13. Wählen Sie in der Spalte **Variablentyp** die Option **Int32**aus. Belassen Sie den Gültigkeits **Bereich** als **while**, und die **Standard** Spalte ist leer.

14. Legen Sie die **Condition** -Eigenschaft der <xref:System.Activities.Statements.While>-Aktivität auf **Index < Items. length;** fest.

15. Ziehen Sie eine <xref:System.Activities.Statements.InvokeDelegate>-Aktivität aus dem Abschnitt **primitive** der Toolbox in den **Text** der Aktivität <xref:System.Activities.Statements.While>.

16. Wählen Sie in der Dropdown-Dropdown-Auflistung **Text** aus.

17. Klicken Sie im **Eigenschaften** Raster für die <xref:System.Activities.Statements.InvokeDelegate> Aktivität auf die **...** -Schaltfläche in der Eigenschaft **Delegatargumente** .

18. Geben Sie in der Spalte **Wert** des Arguments mit dem Namen **Argument**den Wert **Items [index]** ein. Klicken Sie auf **OK** , um das Dialogfeld **delegatearguments** zu schließen.

19. Ziehen Sie eine <xref:System.Activities.Statements.Assign>-Aktivität auf die horizontale Linie unterhalb der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Die <xref:System.Activities.Statements.Assign>-Aktivität wird erstellt, und es wird automatisch eine <xref:System.Activities.Statements.Sequence> Aktivität erstellt, die die beiden Aktivitäten im **Body** -Abschnitt der **myforeach** -Aktivität enthält. Die Sequenz wird benötigt, da der **Text** Abschnitt nur eine einzelne Aktivität enthalten kann. Das automatische Erstellen einer neuen <xref:System.Activities.Statements.Sequence>-Aktivität ist eine neue Funktion von [!INCLUDE[net_v45](../includes/net-v45-md.md)].

20. Legen Sie die Eigenschaft **auf** des <xref:System.Activities.Statements.Assign> Aktivität auf **Index**fest. Legen Sie die **value** -Eigenschaft der **assign** -Aktivität auf **Index + 1**fest.

    Die benutzerdefinierte **myforeach** -Aktivität ruft nun eine beliebige Aktivität einmal für jeden Wert auf, der über die **Items** -Auflistung an Sie übermittelt wird, wobei die Werte in der Auflistung als Eingaben für die Aktivität verwendet werden.

### <a name="use-the-custom-activity-in-a-workflow"></a>Verwenden der benutzerdefinierten Aktivität in einem Workflow

1. Erstellen Sie das Projekt, indem Sie **STRG + UMSCHALT + B**drücken.

2. Öffnen Sie **Workflow1. XAML** in **Projektmappen-Explorer**im Designer.

3. Ziehen Sie eine **myforeach** -Aktivität aus der Toolbox auf die Designer Oberfläche. Die Aktivität befindet sich in einem Abschnitt der Toolbox mit dem gleichen Namen wie das Projekt.

4. Legen Sie die **Items** -Eigenschaft der **myforeach** -Aktivität auf **New Object [] {1, "ABC"}** fest.

5. Ziehen Sie eine <xref:System.Activities.Statements.WriteLine>-Aktivität aus dem Abschnitt **primitive** der Toolbox in den Abschnitt Delegat **: Body** der **myforeach** -Aktivität.

6. Legen Sie die **Text** -Eigenschaft der <xref:System.Activities.Statements.WriteLine>-Aktivität auf " **Argument.-Zeichenfolge ()** " fest.

   Wenn der Workflow ausgeführt wird, wird in der Konsole Folgendes angezeigt:

   **1**
   **abc**
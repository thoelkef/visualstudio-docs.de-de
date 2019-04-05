---
title: 'Vorgehensweise: Definieren und Verarbeiten von aktivitätsdelegaten im Workflow-Designer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37adb6cf6462887010b1c06c7d5af4a539203b15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58962058"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer
[!INCLUDE[net_v45](../includes/net-v45-md.md)] enthält einen neuen vordefinierten Designer für die <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Der Designer kann verwendet werden, um der Aktivität Delegate zuzuweisen, die von <xref:System.Activities.ActivityDelegate>, z. B. <xref:System.Activities.ActivityAction> oder <xref:System.Activities.ActivityFunc%601>, abgeleitet werden.  
  
### <a name="define-an-activity-delegate"></a>Definieren eines Aktivitätsdelegaten  
  
1. In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]Option **Datei**, **neu**, **Projekt**. Wählen Sie die **Workflow** Knoten auf der linken Seite, und die **Konsolenanwendung für Workflows** Vorlage auf der rechten Seite. Nennen Sie das Projekt (falls gewünscht), und klicken Sie auf **Ok**.  
  
2. Mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** , und wählen Sie **hinzufügen**, **neues Element...** . Wählen Sie die **Workflow** Knoten auf der linken Seite, und die **Aktivität** Vorlage auf der rechten Seite. Nennen Sie die neue Aktivität **MyForEach.xaml** , und klicken Sie auf **Ok**. Die Aktivität wird im Workflow-Designer geöffnet.  
  
3. Klicken Sie im Workflow-Designer auf die **Argumente** Registerkarte.  
  
4. Klicken Sie auf **Argument erstellen**. Nennen Sie das neue Argument **Elemente**.  
  
5. In der **Argumenttyp** Spalte **Array von [T]**.  
  
6. Wählen Sie im Typbrowser **Objekt**. Klicken Sie auf **Ok**.  
  
7. Klicken Sie auf **Argument erstellen** erneut aus. Nennen Sie das neue Argument **Text**. In der **Richtung** Spalte für das neue Argument die Option **Eigenschaft**.  
  
8. Wählen Sie in der Spalte Argumenttyp **nach Typen suchen...**  
  
9. Geben Sie im Typbrowser **ActivityAction** in die **Typnamen** Feld. Wählen Sie **ActivityAction\<T >** in der Strukturansicht angezeigt. Wählen Sie **Objekt** in der eingeblendeten-Typ zuzuweisen **ActivityAction\<Objekt >** an das Argument.  
  
10. Ziehen Sie eine <xref:System.Activities.Statements.While> Aktivität aus der **Ablaufsteuerung** Abschnitt der Toolbox auf die Designeroberfläche.  
  
11. Wählen Sie die <xref:System.Activities.Statements.While> -Aktivität, und wählen die **Variablen** Registerkarte.  
  
12. Wählen Sie **erstellen Variable**. Benennen Sie die neue Variable **Index**.  
  
13. In der **Variablentyp** Spalte **Int32**. Lassen Sie die **Bereich** als **während**, und die **Standard** Spalte leer.  
  
14. Legen Sie die **Bedingung** Eigenschaft der <xref:System.Activities.Statements.While> Aktivität **Index < Items.Length;**.  
  
15. Ziehen Sie ein <xref:System.Activities.Statements.InvokeDelegate> Aktivität aus der **primitive** Abschnitt der Toolbox auf die **Text** von der <xref:System.Activities.Statements.While> Aktivität.  
  
16. Wählen Sie **Text** in der Dropdown-Liste von Delegaten.  
  
17. In der **Eigenschaften** Raster für die <xref:System.Activities.Statements.InvokeDelegate> -Aktivität, klicken Sie auf die **...** Schaltfläche der **Delegatargumente** Eigenschaft.  
  
18. In der **Wert** Spalte des Arguments mit dem Namen **Argument**, geben Sie **Items [Index]**. Klicken Sie auf **Ok** schließen die **DelegateArguments** Dialogfeld.  
  
19. Ziehen Sie eine <xref:System.Activities.Statements.Assign>-Aktivität auf die horizontale Linie unterhalb der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Die <xref:System.Activities.Statements.Assign> Aktivität erstellt werden soll, und ein <xref:System.Activities.Statements.Sequence> Aktivität wird automatisch erstellt werden, enthalten die beiden Aktivitäten in der **Text** Teil der **MyForEach** Aktivität. Die Sequenz wird benötigt, da die **Text** Abschnitt kann nur eine einzige Aktivität enthalten. Das automatische Erstellen einer neuen <xref:System.Activities.Statements.Sequence>-Aktivität ist eine neue Funktion von [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
20. Festlegen der **zu** Eigenschaft der <xref:System.Activities.Statements.Assign> Aktivität **Index**. Festlegen der **Wert** Eigenschaft der **zuweisen** Aktivität **Index + 1**.  
  
    Die benutzerdefinierte **MyForEach** -Aktivität ruft nun eine beliebige Aktivität einmal für jeden Wert, der übergeben werden, über die **Elemente** Sammlung mit den Werten in der Auflistung als Eingaben für die Aktivität.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Verwenden der benutzerdefinierten Aktivität in einem Workflow  
  
1. Erstellen Sie das Projekt durch Drücken von **STRG + UMSCHALT + B**.  
  
2. In **Projektmappen-Explorer**öffnen **"Workflow1.xaml"** im Designer.  
  
3. Ziehen Sie eine **MyForEach** Aktivität aus der Toolbox auf die Designeroberfläche. Die Aktivität befindet sich in einem Abschnitt der Toolbox mit dem gleichen Namen wie das Projekt.  
  
4. Legen Sie die **Elemente** Eigenschaft der **MyForEach** Aktivität **new Object [] {1, "Abc"}**.  
  
5. Ziehen Sie eine <xref:System.Activities.Statements.WriteLine> Aktivität aus der **primitive** Abschnitt der Toolbox auf die **Delegate: Body** Teil der **MyForEach** Aktivität.  
  
6. Legen Sie die **Text** Eigenschaft der <xref:System.Activities.Statements.WriteLine> Aktivität **Argument.ToString()**.  
  
   Wenn der Workflow ausgeführt wird, wird in der Konsole Folgendes angezeigt:  
  
   **1**   
   **abc**
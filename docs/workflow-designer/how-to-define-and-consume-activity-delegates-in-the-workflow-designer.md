---
title: "Vorgehensweise: Definieren und Verarbeiten von Aktivit&#228;tsdelegaten im Workflow-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# Vorgehensweise: Definieren und Verarbeiten von Aktivit&#228;tsdelegaten im Workflow-Designer
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] enthält einen neuen vordefinierten Designer für die <xref:System.Activities.Statements.InvokeDelegate>\-Aktivität.Der Designer kann verwendet werden, um der Aktivität Delegate zuzuweisen, die von <xref:System.Activities.ActivityDelegate>, wie <xref:System.Activities.ActivityAction> oder <xref:System.Activities.ActivityFunc%601>, abgeleitet werden.  
  
### Definieren eines Aktivitätsdelegaten  
  
1.  Wählen Sie in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]**Datei**, **Neues Projekt** aus.Wählen Sie den Knoten **Workflow** auf der linken Seite und die Vorlage **Konsolenanwendung für Workflows** auf der rechten Seite aus.Geben Sie dem Projekt \(falls gewünscht\) einen Namen, und klicken Sie auf **Ok**.  
  
2.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen**, **Neues Element** aus.Wählen Sie den Knoten **Workflow** auf der linken Seite und die Vorlage **Aktivität** auf der rechten Seite aus.Nennen Sie die neue Aktivität **MyForEach.xaml**, und klicken Sie auf **OK**.Die Aktivität wird im Workflow\-Designer geöffnet.  
  
3.  Klicken Sie im Workflow\-Designer auf die Registerkarte **Argumente**.  
  
4.  Klicken Sie auf **Argument erstellen**.Nennen Sie das neue Argument **Elemente**.  
  
5.  Wählen Sie in der Spalte **ArgumenttypArray von \[T\]**.  
  
6.  Wählen Sie im Typbrowser die Option **Objekt** aus.Klicken Sie auf **OK**.  
  
7.  Klicken Sie erneut auf **Argument erstellen**.Nennen Sie das neue Argument **Body**.Wählen Sie in der Spalte **Richtung** für das neue Argument die Option **Eigenschaft** aus.  
  
8.  Wählen Sie in der Spalte "Argumenttyp" **Nach Typen suchen…** aus  
  
9. Geben Sie im Typbrowser im Feld **Typname** den Namen **ActivityAction** ein.Wählen Sie in der Strukturansicht **ActivityAction\<T\>**.Wählen Sie im angezeigten Dropdownmenü **Objekt** aus, um den **ActivityAction\<Object\>**\-Typ dem Argument zuzuweisen.  
  
10. Ziehen Sie eine <xref:System.Activities.Statements.While>\-Aktivität aus dem Abschnitt **Control Flow** der Toolbox auf die Designeroberfläche.  
  
11. Wählen Sie die <xref:System.Activities.Statements.While>\-Aktivität aus, und klicken Sie auf die Registerkarte **Variablen**.  
  
12. Wählen Sie **Variable erstellen** aus.Nennen Sie die neue Variable **Index**.  
  
13. Wählen Sie in der Spalte **VariablentypInt32** aus.Verwenden Sie für **BereichWhile**, und lassen Sie die Spalte **Standard** leer.  
  
14. Legen Sie die **Condition**\-Eigenschaft der <xref:System.Activities.Statements.While>\-Aktivität auf **index \< Items.Length;** fest.  
  
15. Ziehen Sie eine <xref:System.Activities.Statements.InvokeDelegate>\-Aktivität aus dem Abschnitt **Primitives** der Toolbox auf den **Text** der <xref:System.Activities.Statements.While>\-Aktivität.  
  
16. Wählen Sie in der Dropdownliste des Delegaten die Option **Textkörper** aus.  
  
17. Klicken Sie im Raster **Eigenschaften** für die <xref:System.Activities.Statements.InvokeDelegate>\-Aktivität auf die Schaltfläche mit den Auslassungszeichen \(**…**\), die sich in der Eigenschaft **Delegatargumente** befindet.  
  
18. In der Spalte **Wert** des Arguments mit dem Namen **Argument** geben Sie **Elemente \[Index\]** ein.Klicken Sie auf **OK**, um das Dialogfeld **DelegateArguments** zu schließen.  
  
19. Ziehen Sie eine <xref:System.Activities.Statements.Assign>\-Aktivität auf die horizontale Linie unterhalb der <xref:System.Activities.Statements.InvokeDelegate>\-Aktivität.Die <xref:System.Activities.Statements.Assign>\-Aktivität wird erstellt, und eine <xref:System.Activities.Statements.Sequence>\-Aktivität wird automatisch erstellt, die die beiden Aktivitäten im Abschnitt **Body** der **MyForEach**\-Aktivität enthält.Die Sequenz wird benötigt, da der Abschnitt **Body** nur eine einzige Aktivität enthalten kann.Das automatische Erstellen einer neuen <xref:System.Activities.Statements.Sequence>\-Aktivität ist eine neue Funktion von [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
20. Legen Sie die **To**\-Eigenschaft der <xref:System.Activities.Statements.Assign>\-Aktivität auf **index** fest.Legen Sie die **Value**\-Eigenschaft der **Assign**\-Aktivität auf **index\+1** fest.  
  
 Die benutzerdefinierte **MyForEach**\-Aktivität ruft nun eine beliebige Aktivität einmal für jeden Wert auf, der durch die **Items**\-Auflistung an sie übergeben wurde. Dabei werden die Werte in der Auflistung als Eingaben für die Aktivität verwendet.  
  
### Verwenden der benutzerdefinierten Aktivität in einem Workflow  
  
1.  Erstellen Sie das Projekt, indem Sie **STRG\+UMSCHALT\+B** drücken.  
  
2.  Öffnen Sie im **Projektmappen\-ExplorerWorkflow1.xaml** im Designer.  
  
3.  Ziehen Sie eine **MyForEach**\-Aktivität aus der Toolbox auf die Designeroberfläche.Die Aktivität befindet sich in einem Abschnitt der Toolbox mit dem gleichen Namen wie das Projekt.  
  
4.  Legen Sie die **Items**\-Eigenschaft der **MyForEach**\-Aktivität auf **new Object\[\] {1, "abc"}** fest.  
  
5.  Ziehen Sie eine <xref:System.Activities.Statements.WriteLine>\-Aktivität aus dem Abschnitt **Primitives** der Toolbox in den Abschnitt **Delegate:Body** der **MyForEach**\-Aktivität.  
  
6.  Legen Sie die **Text**\-Eigenschaft der <xref:System.Activities.Statements.WriteLine>\-Aktivität auf **Argument.ToString\(\)** fest.  
  
 Wenn der Workflow ausgeführt wird, wird in der Konsole Folgendes angezeigt:  
  
 **1**   
**abc**
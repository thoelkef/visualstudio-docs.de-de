---
title: Anpassen der Modell-Explorer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c69cdd822941fd81478fae0b62d509b64ef513da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-the-model-explorer"></a>Anpassen des Modell-Explorers
Sie können das Aussehen und Verhalten des Explorers für den Designer einer domänenspezifischen Sprache wie folgt ändern:  
  
-   Den Titel des Fensters zu ändern.  
  
-   Ändern Sie das Symbol "Tab".  
  
-   Ändern Sie die Symbole für Knoten.  
  
-   Blenden Sie Knoten.  
  
## <a name="changing-the-window-title"></a>Den Titel des Fensters ändern  
 Um dem Fenstertitel des generierter Explorer ändern, wählen **Explorer Verhalten** in der **Explorer für DSL**, und klicken Sie dann in der **Eigenschaften** fest der  **Titel** für den Titel der gewünschten Eigenschaft.  
  
## <a name="changing-the-tab-icon"></a>Ändern das Symbol "Tab"  
 Um das Symbol "Tab" für den Explorer ändern, wird ein 16 x 16-Pixel-Symbol in einer BMP-Datei verwendet. Legen Sie die Symboldatei im Ordner "\DslPackage\Resources\", und ändern Sie den Dateinamen an **ModelExplorerToolWindowBitmaps.bmp**. Sie können z. B. Ändern der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico-Symbol in das BMP-Format der Datei und benennen Sie sie um **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Die generierten-Designer dieses Symbols auf der Registerkarte "Explorer" angedockten zusammen mit **Projektmappen-Explorer**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Festlegen von benutzerdefinierten Symbolen für Explorer-Knoten  
 Sie können Knoten im Explorer mit der Explorer-Knoten-Einstellungen anpassen. Das folgende Verfahren zeigt, wie ein Knoten ein Symbol hinzu.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>So fügen Sie ein Symbol zu einem Explorerknoten hinzu  
  
1.  Erstellen einer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Lösung mithilfe der Datenflusstask Projektmappenvorlage.  
  
2.  Speichern Sie eine BMP-Datei, die in ein 16 x 16-Pixel-Symbol enthält die **Dsl\Resources** Ordner in der Projektmappe.  
  
3.  In der **Explorer für DSL**, mit der rechten Maustaste **Explorer Verhalten** , und klicken Sie dann auf **Hinzufügen neuer Knoten Explorereinstellungen**.  
  
     Ein **ExplorerNodeSettings** Knoten befindet sich unter dem **Knoteneinstellungen für benutzerdefinierte** Knoten.  
  
4.  Wählen Sie **ExplorerNodeSettings**, und klicken Sie dann in der **Eigenschaften** fest **Klasse** auf **Akteur**.  
  
5.  Legen Sie **zum Anzeigen des Symbols** auf den Pfad der Symboldatei.  
  
6.  Transformieren Sie aller Vorlagen erstellen Sie und führen Sie die Projektmappe.  
  
7.  Öffnen Sie das Beispiel-Diagramm, in der generierten Designer.  
  
     Der Explorer sollte drei anzeigen **Akteur** Knoten mit dem Symbol.  
  
> [!NOTE]
>  Wenn Sie ein Symbol "Knoten" für ein bestimmtes Element festgelegt haben, die im generierten-Explorer angezeigt wird, werden alle Explorer-Knoten das Symbol angezeigt. Wenn das Symbol "keine" festgelegt wurde, werden der Knoten das Standardsymbol angezeigt.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Ändern des Namens angezeigt, die auf einem Explorerknoten  
 Sie können ändern, wie die Namen von Modellelementen im Explorer angezeigt werden. Das folgende Verfahren zeigt, wie den Namen des anzuzeigenden der **Aufgabe** , verweist eine **Kommentar** im Knoten "Kommentar".  
  
#### <a name="to-display-a-property"></a>Eine Eigenschaft an  
  
1.  Öffnen Sie die Projektmappe, die Sie im vorherigen Verfahren erstellt haben.  
  
2.  Stellen Sie sicher, dass die **Kommentar** verweist auf nur eine einzelne Domänenklasse durch Festlegen die Multiplizität der Rolle mit Eigenschaftsnamen **Themen** zu 0.. 1. Der Eigenschaftsname sollten werden **Betreff**, sollten Sie den Namen der Beziehung werden **CommentReferencesSubject**.  
  
3.  In der **Explorer für DSL**, mit der rechten Maustaste **Explorer Verhalten** , und klicken Sie dann auf **Hinzufügen neuer Knoten Explorereinstellungen**.  
  
     Ein **ExplorerNodeSettings** Knoten befindet sich unter dem **Knoteneinstellungen für benutzerdefinierte** Knoten.  
  
4.  Wählen Sie **ExplorerNodeSettings**, und klicken Sie dann in der **Eigenschaften** fest **Klasse** auf **Kommentar**.  
  
5.  Mit der rechten Maustaste die **Kommentar** Knoten, und klicken Sie dann auf **neue Eigenschaftspfad hinzufügen**.  
  
     Ein neuer Knoten angezeigt wird, mit dem Namen **Eigenschaft angezeigt**.  
  
6.  Wählen Sie **Eigenschaft angezeigt**, und klicken Sie dann in der **Eigenschaften** Fenster, klicken Sie auf das Wertfeld des **Path-To-Eigenschaft**. Wählen Sie **Kommentar**, klicken Sie dann **CommentReferencesSubject**, klicken Sie dann **FlowElement**. Der resultierende Pfad entspricht in etwa **CommentReferencesSubject.Subject/! Betreff**.  
  
7.  Im Wertefeld der **Eigenschaft**Option **Namen**.  
  
8.  Transformieren Sie aller Vorlagen erstellen Sie und führen Sie die Projektmappe.  
  
9. Öffnen Sie das Beispiel-Diagramm, in der generierten Designer.  
  
10. Zeichnen einer **Kommentar Connector** zwischen dem Kommentar-Element und die **Task1** Elemente des Diagramms.  
  
     Der Explorer-Knoten sollte den Kommentar als anzeigen **Task1**.  
  
## <a name="hiding-nodes"></a>Ausblenden von Knoten  
 Sie können einen Knoten im Explorer ausblenden, indem Sie den Pfad zum Hinzufügen der **Knoten ausgeblendet** Knoten der **Explorer für DSL**. Das folgende Verfahren zeigt, wie Sie ausblenden **Kommentar** Knoten.  
  
#### <a name="to-hide-an-explorer-node"></a>So blenden Sie ein Explorerknoten aus  
  
1.  Öffnen Sie die Projektmappe, die Sie im vorherigen Verfahren erstellt haben.  
  
2.  In der **Explorer für DSL**, mit der rechten Maustaste **Explorer Verhalten** , und klicken Sie dann auf **Pfad der neuen Domäne hinzufügen**.  
  
     Ein **Domänenpfad** Knoten befindet sich unter **Knoten ausgeblendet**.  
  
3.  Wählen Sie **Domänenpfad**, und klicken Sie dann in der **Eigenschaften** Fenster, klicken Sie auf das Wertfeld des **Pfaddefinition**. Wählen Sie **FlowGraph**, klicken Sie dann **FlowGraphHasComments**. Der resultierende Pfad entspricht in etwa **FlowGraphHasComments.Comments**  
  
4.  Transformieren Sie aller Vorlagen erstellen Sie und führen Sie die Projektmappe.  
  
5.  Öffnen Sie das Beispiel-Diagramm, in der generierten Designer.  
  
     Sollte nur im Explorer Anzeigen einer **Akteure** Knoten, und sollte nicht mehr anzeigen der **Kommentare** Knoten.  
  
## <a name="see-also"></a>Siehe auch

[Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
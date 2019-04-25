---
title: Anpassen des Modell-Explorers | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 51e79850e2958ce295ab4d98f3ea191a5222a8fb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078914"
---
# <a name="customizing-the-model-explorer"></a>Anpassen des Modell-Explorers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können das Aussehen und Verhalten des Explorers für Ihre DSL-Designer wie folgt ändern:  
  
- Den Titel des Fensters zu ändern.  
  
- Ändern Sie die Registerkarte.  
  
- Ändern Sie die Symbole für Knoten an.  
  
- Blenden Sie Knoten aus.  
  
## <a name="changing-the-window-title"></a>Den Titel des Fensters ändern  
 Um dem Fenstertitel des generierter Explorer ändern, wählen **Explorer-Verhalten** in die **DSL-Explorer**, und klicken Sie dann in der **Eigenschaften** legen die  **Titel** Eigenschaft, um den Titel werden sollen.  
  
## <a name="changing-the-tab-icon"></a>Ändern die Registerkarte "-Symbol  
 Um das Registerkartensymbol für den Explorer ändern, verwenden Sie eine 16 x 16-Pixel-Symbol in BMP-Datei ein. Legen Sie die Symboldatei im Ordner "\DslPackage\Resources\", und ändern Sie dann auf den Dateinamen an **ModelExplorerToolWindowBitmaps.bmp**. Sie können z. B. Ändern der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] setup.ico-Symbol-Datei in das BMP-Format, und benennen Sie sie in **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Der generierte Designer wird dieses Symbol auf der Registerkarte "Explorer" angezeigt, zusammen mit angedockten **Projektmappen-Explorer**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Festlegen von benutzerdefinierten Symbolen für Explorer-Knoten  
 Sie können Knoten im Explorer mit der Explorer-knoteneinstellungen anpassen. Das folgende Verfahren zeigt ein Symbol mit einem Knoten hinzufügen.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Ein Explorerknoten ein Symbol hinzu  
  
1. Erstellen Sie eine [!INCLUDE[dsl](../includes/dsl-md.md)] Lösung mithilfe der Lösungsvorlage Aufgabenfluss.  
  
2. Speichern Sie eine BMP-Datei, die in ein 16 x 16-Pixel-Symbol enthält die **dsl\ressourcen** Ordner in der Projektmappe.  
  
3. In der **DSL-Explorer**, mit der rechten Maustaste **Explorer-Verhalten** , und klicken Sie dann auf **fügen neue Explorer-Knoteneinstellungen**.  
  
     Ein **ExplorerNodeSettings** Knoten befindet sich unter dem **benutzerdefinierte Knoteneinstellungen** Knoten.  
  
4. Wählen Sie **ExplorerNodeSettings**, und klicken Sie dann in der **Eigenschaften** legen **Klasse** zu **Actor**.  
  
5. Legen Sie **zum Anzeigen des Symbols** auf den Pfad der Symboldatei.  
  
6. Transformieren Sie alle Vorlagen, und klicken Sie dann erstellen Sie, und führen Sie die Projektmappe.  
  
7. Öffnen Sie im generierten Designer das Beispiel-Diagramm.  
  
     Im Explorer sollte angezeigt werden drei **Actor** Knoten mit dem Symbol.  
  
> [!NOTE]
>  Wenn Sie ein Symbol "Knoten" für jedes Element festgelegt haben, die im generierten-Explorer angezeigt wird, werden alle Explorer-Knoten das Symbol angezeigt. Wenn das Symbol "keine" festgelegt wurde, werden der Knoten das Standardsymbol angezeigt.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Ändern des Namens angezeigt, die auf einem Explorerknoten  
 Sie können ändern, wie die Namen von Modellelementen im Explorer angezeigt werden. Das folgende Verfahren zeigt, wie Sie den Namen des Anzeigen der **Aufgabe** auf den verwiesen wird durch eine **Kommentar** im Knoten "Kommentar".  
  
#### <a name="to-display-a-property"></a>Eine Eigenschaft an  
  
1. Öffnen Sie die Projektmappe, die Sie im vorherigen Verfahren erstellt haben.  
  
2. Stellen Sie sicher, dass die **Kommentar** verweist auf nur eine einzelne Domäne-Klasse durch die Multiplizität der Rolle mit dem Eigenschaftsnamen festlegen **Themen** auf 0.. 1. Namen der Eigenschaft sollte werden **Betreff**, und den Namen der Beziehung sollte werden **CommentReferencesSubject**.  
  
3. In der **DSL-Explorer**, mit der rechten Maustaste **Explorer-Verhalten** , und klicken Sie dann auf **fügen neue Explorer-Knoteneinstellungen**.  
  
     Ein **ExplorerNodeSettings** Knoten befindet sich unter dem **benutzerdefinierte Knoteneinstellungen** Knoten.  
  
4. Wählen Sie **ExplorerNodeSettings**, und klicken Sie dann in der **Eigenschaften** legen **Klasse** zu **Kommentar**.  
  
5. Mit der rechten Maustaste die **Kommentar** Knoten, und klicken Sie dann auf **Hinzufügen neuer Eigenschaftspfad**.  
  
     Ein neuer Knoten wird angezeigt, mit dem Namen **Eigenschaft angezeigt**.  
  
6. Wählen Sie **Eigenschaft angezeigt**, und klicken Sie dann in der **Eigenschaften** Fenster klicken Sie auf das Wertfeld **Pfad (Eigenschaft),**. Wählen Sie **Kommentar**, klicken Sie dann **CommentReferencesSubject**, klicken Sie dann **FlowElement**. Der resultierende Pfad entspricht in etwa **CommentReferencesSubject.Subject/! Betreff**.  
  
7. Klicken Sie im Feld mit Wert **Eigenschaft**Option **Namen**.  
  
8. Transformieren Sie alle Vorlagen, und klicken Sie dann erstellen Sie, und führen Sie die Projektmappe.  
  
9. Öffnen Sie im generierten Designer das Beispiel-Diagramm.  
  
10. Zeichnen einer **Kommentar Connector** zwischen den Comment-Element und die **Task1** Element im Diagramm.  
  
     Der Explorer-Knoten sollte den Kommentar als anzeigen **Task1**.  
  
## <a name="hiding-nodes"></a>Wenn Knoten ausgeblendet werden  
 Sie können einen Knoten im Explorer ausblenden, indem Sie den Pfad zum Hinzufügen der **ausgeblendete Knoten** Knoten die **DSL-Explorer**. Das folgende Verfahren zeigt, wie Sie ausblenden **Kommentar** Knoten.  
  
#### <a name="to-hide-an-explorer-node"></a>So blenden Sie ein Explorerknoten aus.  
  
1. Öffnen Sie die Projektmappe, die Sie im vorherigen Verfahren erstellt haben.  
  
2. In der **DSL-Explorer**, mit der rechten Maustaste **Explorer-Verhalten** , und klicken Sie dann auf **Pfad der neuen Domäne hinzufügen**.  
  
     Ein **Domänenpfad** Knoten befindet sich unter **ausgeblendete Knoten**.  
  
3. Wählen Sie **Domänenpfad**, und klicken Sie dann in der **Eigenschaften** Fenster klicken Sie auf das Wertfeld **Pfaddefinition**. Wählen Sie **FlowGraph**, klicken Sie dann **FlowGraphHasComments**. Der resultierende Pfad entspricht in etwa **FlowGraphHasComments.Comments**  
  
4. Transformieren Sie alle Vorlagen, und klicken Sie dann erstellen Sie, und führen Sie die Projektmappe.  
  
5. Öffnen Sie im generierten Designer das Beispiel-Diagramm.  
  
     Im Explorer sollte nur dann angezeigt, eine **Actors** Knoten, und sollte nicht anzeigen der **Kommentare** Knoten.  
  
## <a name="see-also"></a>Siehe auch  
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

---
title: "Anpassen des Modell-Explorers | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.explorerbehavior"
helpviewer_keywords: 
  - "Domänenspezifische Sprachtools, Domänenspezifische Sprache – Explorer"
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 20
caps.handback.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Anpassen des Modell-Explorers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Darstellung und das Verhalten des Explorers für den domänenspezifischen Sprache Designer wie folgt ändern:  
  
-   Ändern Sie den Fenstertitel.  
  
-   Ändern Sie das Symbol Registerkarten.  
  
-   Ändern Sie die Symbole für Knoten verwendet.  
  
-   Ausblenden.  
  
## Der Fenstertitel ändert  
 Um den Fenstertitel des generierten Explorer zu ändern, legen Sie die Option **Explorer\-Verhalten** in **DSL\-Explorer**und anschließend im Fenster **Eigenschaften** , die **Titel**\-Eigenschaft auf den Namen fest, den Sie verwenden möchten.  
  
## Das Ändern Registerkarten\-Symbol  
 Um das Symbol für den Registerkarten Projektmappen\-Explorer zu ändern, verwenden Sie ein Symbol mit 16 × 16 Pixeln in eine BMP\-Datei.  Setzen Sie die Symboldatei in DslPackage \\ \\ Resources \\ ein, und ändern Sie dann den Dateinamen in ModelExplorerToolWindowBitmaps.bmp.  Beispielsweise können Sie die Symboldatei [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico .bmp\-Format zu ändern und sie an DSLLanguageName DslPackage \\ Resources \\ \\ ModelExplorerToolWindowBitmaps.bmp umbenennen.  Der generierte Designer zeigt dieses Symbol auf der Registerkarte im Explorer angezeigt, wenn sie zusammen mit **Projektmappen\-Explorer**angedockt wird.  
  
## Symbole aufgelistet Einstellungs\-benutzerdefinierte Explorer\-Knoten  
 Sie können Knoten im Projektmappen\-Explorer den Knoten Projektmappen\-Explorer anpassen, indem Sie Einstellungen verwenden.  Das folgende Verfahren zeigt, wie Sie ein Symbol eines Knotens hinzufügt.  
  
#### So legen Sie ein Symbol im Projektmappen\-Explorer einen Knoten hinzu  
  
1.  Erstellen Sie eine [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Projektmappe, indem Sie die Vorlage Aufgaben\-Fluss Office\-Lösungen verwenden.  
  
2.  Fügen Sie eine BMP\-Datei, das ein Symbol mit 16 × 16 Pixeln im **Dsl\\Resources** Ordner in der Projektmappe enthält.  
  
3.  In **DSL\-Explorer**mit der rechten Maustaste auf **Explorer\-Verhalten** , und klicken Sie dann auf **Neue Explorer\-Knoteneinstellungen hinzufügen**.  
  
     Ein **ExplorerNodeSettingsBenutzerdefinierte Knoteneinstellungen** Knoten unter dem Knoten angezeigt wird.  
  
4.  Wählen Sie **ExplorerNodeSettings**und anschließend im Fenster **Eigenschaften** , legen Sie **Akteur**zu **Klasse** fest.  
  
5.  Legen Sie **Anzuzeigendes Symbol** auf den Pfad der Symboldatei fest.  
  
6.  Transformieren Sie alle Vorlagen, und erstellen Sie die Projektmappe, und führen Sie sie aus.  
  
7.  Im generierten Designer öffnen Sie das Diagramm. B.  
  
     Im Projektmappen\-Explorer sollte **Akteur** drei Knoten anzeigen, die das Symbol haben.  
  
> [!NOTE]
>  Wenn Sie ein Symbol Knoten für ein Element festgelegt haben, das im generierten Explorer angezeigt werden, zeigen alle Knoten Projektmappen\-Explorer das Symbol an.  Ist kein Symbol festgelegt wurde, werden die Knoten das Standardsymbol angezeigt.  
  
## Ändern des Namens auf einem angezeigten Explorer\-Knoten  
 Sie können ändern, wie die Namen von Modellelementen im Projektmappen\-Explorer angezeigt werden.  Das folgende Verfahren zeigt, wie Sie den Namen der Aufgabe angezeigt, die durch einen Kommentar im Kommentarknoten verwiesen wird.  
  
#### Um eine Eigenschaft anzeigen  
  
1.  Öffnen Sie die Projektmappe aus, die Sie in der vorherigen Prozedur erstellt haben.  
  
2.  Überprüfen Sie, ob der Kommentar nur eine Domänenklasse verweist, indem Sie die Multiplizität der Rolle mit Eigenschaftennamen **Betreffe** auf 0..1 festlegen.  Der Eigenschaftenname soll **Betreff**werden. Der Beziehungsname soll **CommentReferencesSubject**werden.  
  
3.  In **DSL\-Explorer**mit der rechten Maustaste auf **Explorer\-Verhalten** , und klicken Sie dann auf **Neue Explorer\-Knoteneinstellungen hinzufügen**.  
  
     Ein **ExplorerNodeSettingsBenutzerdefinierte Knoteneinstellungen** Knoten unter dem Knoten angezeigt wird.  
  
4.  Wählen Sie **ExplorerNodeSettings**und anschließend im Fenster **Eigenschaften** , legen Sie **Kommentar**zu **Klasse** fest.  
  
5.  **Kommentar** der rechten Maustaste auf den Knoten, und klicken Sie anschließend auf **Neuen Eigenschaftspfad hinzufügen**.  
  
     Ein neuer Knoten angezeigt, der **Angezeigte Eigenschaft**benannt ist.  
  
6.  Wählen Sie **Angezeigte Eigenschaft**und anschließend im Fenster **Eigenschaften** , klicken Sie auf das Feld Wert von **Pfad zu Eigenschaft**.  Wählen Sie **Kommentar**, **CommentReferencesSubject**, **FlowElement**.  Der resultierende Pfad sollte **CommentReferencesSubject.Subject\/\!Betreff**ähneln.  
  
7.  Klicken Sie im Feld Wert den Eintrag **Eigenschaft**von **Name**.  
  
8.  Transformieren Sie alle Vorlagen, und erstellen Sie die Projektmappe, und führen Sie sie aus.  
  
9. Im generierten Designer öffnen Sie das Diagramm. B.  
  
10. Zeichnen Sie **Kommentarkonnektor** Kommentar zwischen dem Element und dem **Task1**\-Element im Diagramm.  
  
     Der Projektmappen\-Explorer den Knoten sollte als Kommentar **Task1**anzeigen.  
  
## Ausblenden von Knoten  
 Sie können einen Knoten im Explorer auszublenden, indem Sie den entsprechenden Pfad für die **Ausgeblendete KnotenDSL\-Explorer**Knoten hinzufügen.  Das folgende Verfahren zeigt, wie Kommentarknoten ausblendet.  
  
#### So blenden Projektmappen\-Explorer den Knoten  
  
1.  Öffnen Sie die Projektmappe aus, die Sie in der vorherigen Prozedur erstellt haben.  
  
2.  In **DSL\-Explorer**mit der rechten Maustaste auf **Explorer\-Verhalten** , und klicken Sie dann auf **Neuen Domänenpfad hinzufügen**.  
  
     Ein **Domänenpfad** Knoten wird unter **Ausgeblendete Knoten**.  
  
3.  Wählen Sie **Domänenpfad**und anschließend im Fenster **Eigenschaften** , klicken Sie auf das Feld Wert von **Pfaddefinition**.  Wählen Sie **FlowGraph**, **FlowGraphHasComments**.  Der resultierende Pfad sollte etwa folgendermaßen aussehen **FlowGraphHasComments.Comments**  
  
4.  Transformieren Sie alle Vorlagen, und erstellen Sie die Projektmappe, und führen Sie sie aus.  
  
5.  Im generierten Designer öffnen Sie das Diagramm. B.  
  
     Im Projektmappen\-Explorer sollte nur einen **Akteure** Knoten anzeigen und sollte den **Kommentare** Knoten nicht anzeigen.  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)
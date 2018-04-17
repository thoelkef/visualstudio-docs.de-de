---
title: 'Vorgehensweise: Erstellen Sie eine Zustandsautomat-Workflowbibliothek (Vorgängerversion) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8220c6e9dbd2d97e0bf1017498ca3b295424863
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Vorgehensweise: Erstellen einer Zustandsautomatworkflowbibliothek (Vorgängerversion)

Befolgen Sie diese Schritte zum Erstellen eines Zustandsautomat-Workflowbibliothek-Projekts mit älteren Windows Workflow-Designer bereitgestellten [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.

### <a name="to-create-a-state-machine-workflow-library-project"></a>So erstellen Sie ein Projekt für eine Zustandsautomatworkflowbibliothek:

1.  Starten Sie Visual Studio.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  Wählen Sie entweder die **.NET Framework 3.0** Option oder der **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster aus, um den Designer der Vorgängerversion zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

4.  In der **Projekttypen** Bereich, die Option Visual c# oder Visual Basic (unter **andere Sprachen**) und wählen Sie dann **Workflow**.

5.  In der **Vorlagen** klicken Sie im Bereich **Zustandsautomat-Workflowbibliothek**.

6.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.

7.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.

     Wenn Sie ein Projektmappenverzeichnis für das Projekt erstellt werden soll, wählen Sie die **Projektmappenverzeichnis erstellen** Kontrollkästchen und geben Sie einen Namen in der **Projektmappenname** Feld.

8.  Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)
- [Zustandsautomatworkflows](/dotnet/framework/windows-workflow-foundation/state-machine-workflows)
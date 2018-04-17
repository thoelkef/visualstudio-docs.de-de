---
title: 'Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: faa7c593d27474c0980e7c7df7bf932bd2d5431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-activity-library"></a>Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek
Benutzerdefinierte Aktivitäten werden verwendet, um bestimmte Geschäftsprozesse in einem Workflow zu modellieren. Die Vorlage Aktivitätsbibliothek in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] wurde bereitgestellt, damit Sie solche benutzerdefinierten Aktivitäten visuell mithilfe der Windows-Workflow-Designer erstellen können.

### <a name="to-create-a-workflow-activity-library"></a>So erstellen Sie eine Workflowaktivitätsbibliothek

1.  Starten Sie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Auf der **Datei** Sie im Menü **neu**, und wählen Sie dann **Projekt...** .

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  In der **Projekttypen** klicken Sie im Bereich **Workflow** entweder aus der **Visual C#-** Projekte oder **Visual Basic** Gruppierungen je nach Ihrer Bevorzugte Sprache.

4.  In der **Vorlagen** klicken Sie im Bereich **Aktivitätsbibliothek**.

5.  In der **Namen** Feld geben einen beschreibenden Namen für das Projekt, um es einfach identifizieren zu können.

6.  In der **Speicherort** den Suchbegriff in das Verzeichnis, in dem Sie das Projekt speichern, oder klicken Sie auf möchten **Durchsuchen** navigieren.

7.  In der **Lösung** Feld, geben Sie einen beschreibenden Namen für die Projektmappe, und klicken Sie auf **OK**.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], klicken Sie mit der mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann **Neues Projekt...** So öffnen die **neues Projekt** (Dialogfeld). Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8.  Die Projektvorlage erstellt eine Aktivitätsdefinition im XAML-Format. Windows Workflow-Designer wird geöffnet und zeigt den Zeichenbereich für die benutzerdefinierte Aktivität.

9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfsoberfläche, um sie in die benutzerdefinierte Aktivität aufzunehmen.

    > [!CAUTION]
    > Sie können nur eine untergeordnete Aktivität dem Text der benutzerdefinierten Aktivität hinzufügen. Diese untergeordnete Aktivität kann jedoch eine zusammengesetzte Aktivität sein, z. B. eine <xref:System.Activities.Statements.Sequence>-Aktivität oder <xref:System.Activities.Statements.Flowchart>-Aktivität.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen einer Aktivität](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
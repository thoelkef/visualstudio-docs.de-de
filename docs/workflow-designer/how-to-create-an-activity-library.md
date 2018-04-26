---
title: 'Workflow-Designer - Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef62a5098581042a4995d6c522e0757c361e9d4f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-activity-library"></a>Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek
Benutzerdefinierte Aktivitäten werden verwendet, um bestimmte Geschäftsprozesse in einem Workflow zu modellieren. Die Vorlage Aktivitätsbibliothek in Visual Studio 2010 wurde bereitgestellt, damit Sie solche benutzerdefinierten Aktivitäten visuell mithilfe der Windows-Workflow-Designer erstellen können.

### <a name="to-create-a-workflow-activity-library"></a>So erstellen Sie eine Workflowaktivitätsbibliothek

1.  Starten Sie Visual Studio 2010.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  In der **Projekttypen** klicken Sie im Bereich **Workflow** entweder aus der **Visual C#-** Projekte oder **Visual Basic** Gruppierungen je nach Ihrer Bevorzugte Sprache.

4.  In der **Vorlagen** klicken Sie im Bereich **Aktivitätsbibliothek**.

5.  In der **Namen** Feld geben einen beschreibenden Namen für das Projekt, um es einfach identifizieren zu können.

6.  In der **Speicherort** den Suchbegriff in das Verzeichnis, in dem Sie das Projekt speichern, oder klicken Sie auf möchten **Durchsuchen** navigieren.

7.  In der **Lösung** Feld, geben Sie einen beschreibenden Namen für die Projektmappe, und klicken Sie auf **OK**.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in Visual Studio 2010, klicken Sie mit der mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann  **Neues Projekt** So öffnen die **neues Projekt** (Dialogfeld). Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8.  Die Projektvorlage erstellt eine Aktivitätsdefinition im XAML-Format. Windows Workflow-Designer wird geöffnet und zeigt den Zeichenbereich für die benutzerdefinierte Aktivität.

9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfsoberfläche, um sie in die benutzerdefinierte Aktivität aufzunehmen.

    > [!CAUTION]
    > Sie können nur eine untergeordnete Aktivität dem Text der benutzerdefinierten Aktivität hinzufügen. Diese untergeordnete Aktivität kann jedoch eine zusammengesetzte Aktivität sein, z. B. eine <xref:System.Activities.Statements.Sequence>-Aktivität oder <xref:System.Activities.Statements.Flowchart>-Aktivität.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen einer Aktivität](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
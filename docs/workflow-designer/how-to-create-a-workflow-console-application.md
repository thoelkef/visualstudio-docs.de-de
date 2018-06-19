---
title: 'Workflow-Designer - Vorgehensweise: erstellen eine Konsolenanwendung für Workflows'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970899"
---
# <a name="how-to-create-a-workflow-console-application"></a>Vorgehensweise: Erstellen einer Konsolenanwendung für Workflows

Windows Workflow Foundation (WF) können Sie Workflows zum Ausführen von Systemprozessen oder menschlichen Prozessen erstellen. Windows Workflow-Designer stellt die Entwurfsoberfläche zum Erstellen dieser Workflows an. Workflow-Designer zum Erstellen von Workflows von innerhalb von Visual Studio verwendet werden können, oder er kann in andere Anwendungen, die den Designer neu hosten integriert werden.

In diesem Thema wird beschrieben, wie Workflow-Designer in Visual Studio 2010 verwenden, um einen Workflow in einer Konsolenanwendung zu erstellen.

## <a name="to-create-a-workflow-console-application"></a>So erstellen Sie eine Konsolenanwendung für Workflows

1.  Starten Sie Visual Studio 2010.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  In der **installierte Vorlagen** klicken Sie im Bereich **Workflow** entweder aus der **Visual C#-** oder **Visual Basic** Gruppierungen, abhängig von Ihrer bevorzugter Sprache.

4.  Wählen Sie im mittleren Bereich **Workflowkonsolenanwendung**.

5.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.

6.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.

7.  In der **Lösung** Geben Sie den Namen für die neue Projektmappe. Klicken Sie auf **OK** zum Erstellen der Anwendung.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in Visual Studio 2010, klicken Sie mit der mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann  **Neues Projekt** So öffnen die **neues Projekt** (Dialogfeld). Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8.  Die Projektvorlage erstellt eine Workflowdefinition in XAML, und die Konsolenanwendungsdefinition ist in Quellcode. Workflow-Designer wird geöffnet und zeigt den Canvas für den Workflow, den Sie erstellt haben.

9. Um einen Workflow zu verfassen, ziehen Sie Aktivitäten oder andere Workflowelemente von der **Toolbox** auf die Entwurfsoberfläche in Ihrem Workflow.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
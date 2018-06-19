---
title: 'Workflow-Designer - Vorgehensweise: Erstellen von Konsolenanwendungen für sequenzielle Workflows (Vorgängerversion)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb4e048fdf8eb8fee541f84656a29427b5a07a1d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973218"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Vorgehensweise: Erstellen von Konsolenanwendungen für sequenzielle Workflows (Vorgängerversion)

Führen Sie diese Schritte zum Erstellen einer Konsolenanwendung für sequenzielle Workflow-Projekt mithilfe der Vorgängerversion Windows Workflow-Designer bereitgestellter von Visual Studio 2010. Verwenden Sie die legacy-Workflow-Designer, wenn Sie .NET Framework, Version 3.5 oder die WinFX abzielen möchten.

## <a name="to-create-a-sequential-workflow-console-application"></a>So erstellen Sie eine Konsolenanwendung für sequenzielle Workflows

1.  Starten Sie Visual Studio.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  Wählen Sie entweder die **.NET Framework 3.0** Option oder der **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster aus, um den Designer der Vorgängerversion zuzugreifen.

    > [!NOTE]
    > Ist die Standardoption in Visual Studio 2010 **.NET Framework 4**. Diese Option dient zum Erstellen von Windows Workflow Foundation (WF)-Anwendungen, die auf .NET Framework 4 abzielen, und es werden keine der Designer den Vorgängerversion verwendet.

4.  In der **Projekttypen** Bereich Option Visual C#-Projekte oder Visual Basic-Projekte (unter **andere Sprachen**), und wählen Sie dann **Workflow**.

5.  In der **Vorlagen** klicken Sie im Bereich **Konsolenanwendung für sequenzielle Workflows**.

6.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.

7.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.

     Der Windows Forms-Designer wird geöffnet und zeigt Form1 des neu erstellten Projekts an.

8.  Klicken Sie auf **OK**.

     Der Workflow-Designer wird geöffnet und zeigt die Workflowentwurfsoberfläche des neu erstellten sequenziellen Workflows an.

9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfsoberfläche in die **Aktivität ablegen** festgelegten Bereich.

## <a name="see-also"></a>Siehe auch

- [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)
- [Entwickeln von Workflows](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)
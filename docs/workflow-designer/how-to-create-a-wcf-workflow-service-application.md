---
title: 'Workflow-Designer - Vorgehensweise: erstellen eine Dienstanwendung für WCF-Workflow'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93fb69862c228a3b6e61467facba188dd20c67c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974668"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Vorgehensweise: Erstellen einer Dienstanwendung für WCF-Workflows

Windows Communication Foundation (WCF)-workflowdienstanwendungen sind verteilte Kommunikationsdienste, die Nachrichten zwischen Clients und untereinander über Prozessgrenzen hinweg zu übergeben. Die Implementierung des Dienstvertrags auf der Dienstseite erfolgt deklarativ über Workflowaktivitäten in .NET Framework 4 im analog zu den früheren Workflowdiensten in .NET Framework 3.5.

## <a name="to-create-a-wcf-workflow-service-application"></a>So erstellen Sie eine WCF-Workflowdienstanwendung

1.  Starten Sie Visual Studio 2010.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3.  In der **installierte Vorlagen** klicken Sie im Bereich **WCF** oder **Workflow** entweder aus der **Visual C#-** oder **Visual Basic** Gruppierungen je nach bevorzugter Sprache.

4.  Wählen Sie im mittleren Bereich **WCF-Workflowdienstanwendung**.

5.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.

6.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.

7.  In der **Lösung** Feld aus, wählen Sie entweder eine neue Projektmappe erstellen, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in Visual Studio 2010, klicken Sie mit der mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann  **Neues Projekt** So öffnen die **neues Projekt** (Dialogfeld). Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8.  Die Projektvorlage erstellt eine Dienstdefinition im XAML-Format. Windows Workflow-Designer wird geöffnet, in die Entwurfsansicht mit einer <xref:System.Activities.Statements.Sequence> Aktivität, die einen Satz von enthält <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen einer Aktivität](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
---
title: Erstellen Sie ein Workflow Foundation-Projekt
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0450260d5d889c141607a281740bf06d255d5c17
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923420"
---
# <a name="workflow-project-templates"></a>Workflow-Projektvorlagen

Sie können die Workflows, Windows Communication Foundation (WCF)-Workflowdienste, benutzerdefinierte Aktivitäten und benutzerdefinierte Aktivitätsdesigner mit Visual Studio-Projektvorlagen erstellen. In diesem Artikel wird beschrieben, wie zum Erstellen von Bibliotheken und Anwendungen mit den Projektvorlagen in Visual Studio verfügbar wird.

## <a name="create-a-workflow-project"></a>Erstellen eines Workflowprojekts

Visual Studio bietet vier verschiedene Vorlagen für die Workflow-Projekt:

- Workflow-Konsolen-app

- WCF Workflow Service-app

- Aktivitätsbibliothek

- Aktivitäts-designerbibliothek

Installieren Sie zuerst diese Vorlagen für den Zugriff auf die **Windows Workflow Foundation** Komponente von Visual Studio 2017. Ausführliche Anweisungen finden Sie unter [Installieren von Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Nach der Installation der **Windows Workflow Foundation** Komponente, öffnen die **neues Projekt** Dialogfeld dazu **Datei** > **neu**  >  **Projekt**.

1. Wählen Sie im linken Bereich die **Visual C#-** > **Workflow** Kategorie (oder **Visual Basic** > **Workflow**, wenn Sie Visual Basic bevorzugen).

1. Wählen Sie im mittleren Bereich eine Projektvorlage, z. B. **Konsolenanwendung für Workflows**.

1. In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.

1. In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder wählen möchten **Durchsuchen** dorthin navigieren.

1. In der **Lösung** Geben Sie den Namen für die neue Projektmappe. Wählen Sie **OK** zum Erstellen der Anwendung.

   > [!NOTE]
   > Wenn Sie ein neues Projekt zu einer vorhandenen Projektmappe hinzufügen möchten, öffnen Sie die Projektmappe in Visual Studio, mit der rechten Maustaste in der Lösung in **Projektmappen-Explorer**, und wählen Sie **hinzufügen** > **neu Projekt** zum Öffnen der **neues Projekt** Dialogfeld.

## <a name="workflow-console-app"></a>Workflow-Konsolen-app

Bei Auswahl der **Konsolenanwendung für Workflows** Visual Studio-Vorlage erstellt eine Workflowdefinition in XAML. Der Workflow-Designer wird geöffnet und zeigt den Canvas für den Workflow, die, den Sie erstellt haben. Um einen Workflow zu verfassen, ziehen Sie die Aktivitäten oder andere Workflowelemente von **Toolbox** auf die Entwurfsoberfläche.

## <a name="wcf-workflow-service-app"></a>WCF Workflow Service-app

Bei Auswahl der **WCF-Workflowdienstanwendung** Visual Studio-Vorlage erstellt eine Dienstdefinition im XAML. Der Workflow-Designer wird geöffnet, in die Entwurfsansicht mit einer <xref:System.Activities.Statements.Sequence> Aktivität, die einen Satz von enthält <xref:System.ServiceModel.Activities.Receive> und <xref:System.ServiceModel.Activities.SendReply> Aktivitäten.

## <a name="activity-library"></a>Aktivitätsbibliothek

Bei Auswahl der **Aktivitätsbibliothek** Visual Studio-Vorlage erstellt eine Aktivitätsdefinition im XAML. Workflow-Designer wird geöffnet und zeigt den Canvas für die benutzerdefinierte Aktivität. Ziehen Sie eine Aktivität aus **Toolbox** auf die Entwurfsoberfläche, um sie in Ihre benutzerdefinierte Aktivität aufzunehmen.

> [!NOTE]
> Sie dürfen nur eine untergeordnete Aktivität im Text der benutzerdefinierten Aktivität. Diese untergeordnete Aktivität kann jedoch sein eine zusammengesetzte Aktivität, z. B. eine <xref:System.Activities.Statements.Sequence> Aktivität oder <xref:System.Activities.Statements.Flowchart> Aktivität.

## <a name="activity-designer-library"></a>Aktivitäts-designerbibliothek

Bei Auswahl der **Aktivitäts-Designerbibliothek** Visual Studio-Vorlage erstellt eine aktivitätsdesignerdefinition in XAML und ein Code-Behind-Implementierungsdatei. Der Workflow-Designer wird geöffnet und zeigt den Canvas für den Aktivitätsdesigner. Ziehen Sie Windows Presentation Foundation (WPF)-Steuerelemente aus **Toolbox** auf die Entwurfsoberfläche, um sie in Ihrer benutzerdefinierten Aktivitäts-Designer verwenden.

Ein Beispiel zum Implementieren eines benutzerdefinierten Aktivitätsdesigners finden Sie unter [Vorgehensweise: Erstellen ein benutzerdefinierten Aktivitätsdesigners](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Benutzerdefinierte Aktivitätsdesigner können für benutzerdefinierte Aktivitäten und für Standardaktivitäten für die .NET Framework verwendet werden.

## <a name="see-also"></a>Siehe auch

- [Verwenden Sie den Workflowdesigner](developing-applications-with-the-workflow-designer.md)
- [Entwerfen von Workflows ((.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
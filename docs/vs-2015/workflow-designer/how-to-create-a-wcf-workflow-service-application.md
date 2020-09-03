---
title: 'Vorgehensweise: Erstellen einer WCF-Workflow Dienst Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bf941babd943c6856809a13de847b62745b2056
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72605014"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Vorgehensweise: Erstellen einer Dienstanwendung für WCF-Workflows
[!INCLUDE[indigo1](../includes/indigo1-md.md)]-Workflowdienstanwendungen sind verteilte Kommunikationsdienste, die prozessübergreifend Nachrichten zwischen Clients und untereinander übergeben. Die Implementierung des Dienstvertrags auf der Dienstseite erfolgt deklarativ über Workflowaktivitäten in [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], analog zu den früheren Workflowdiensten in .NET Framework 3.5.

### <a name="to-create-a-wcf-workflow-service-application"></a>So erstellen Sie eine WCF-Workflowdienstanwendung

1. Starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Zeigen Sie im Menü **Datei** auf **neu**, und wählen Sie dann **Projekt...** aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie im Bereich **installierte Vorlagen** in Abhängigkeit von der gewünschten Sprache entweder **WCF** oder **Workflow** aus der **Visual c#** -oder **Visual Basic** Gruppierungen aus.

4. Wählen Sie im mittleren Bereich die Option **WCF-Workflow Dienst Anwendung**aus.

5. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

6. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

7. Wählen Sie **im Feldprojekt** Mappe aus, um eine neue Projekt Mappe zu erstellen, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projekt Mappe eine Workflow Konsolenanwendung hinzufügen möchten, öffnen Sie diese Projekt Mappe in [!INCLUDE[vs2010](../includes/vs2010-md.md)] , klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Projekt Mappe, und wählen Sie **Hinzufügen**und dann **Neues Projekt...** , um das Dialogfeld **Neues Projekt** zu öffnen. Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8. Die Projektvorlage erstellt eine Dienstdefinition im XAML-Format. Der [!INCLUDE[wfd1](../includes/wfd1-md.md)] wird in der Entwurfsansicht mit einer <xref:System.Activities.Statements.Sequence>-Aktivität geöffnet, die einen Satz von <xref:System.ServiceModel.Activities.Receive>-Aktivitäten und <xref:System.ServiceModel.Activities.SendReply>-Aktivitäten enthält.

## <a name="see-also"></a>Weitere Informationen
 Vorgehens [Weise: Erstellen einer Aktivität erstellen](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [eines Workflow Projekts](../workflow-designer/creating-a-workflow-project.md)
---
title: 'Workflow-Designer - Vorgehensweise: Hinzufügen eines neuen Elements zu einem Workflowprojekt'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0aa2be7fd8ecccbd8de0aa54c2693dd6b02c7e10
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Gewusst wie: Hinzufügen eines neuen Elements zu einem Workflowprojekt

Nachdem Sie ein Workflowprojekt erstellt haben, können Sie die Workflowaktivitäten, Designer und andere vertraute Visual Studio-Elemente zu Ihrem Projekt hinzufügen.

Die folgende Tabelle enthält die Windows Workflow Foundation (WF)-Elemente, die Sie zu einem Workflowprojekt hinzufügen können.

|name|Beschreibung|
|----------|-----------------|
|Aktivität|Eine Aktivität, die aus anderen Aktivitäten besteht. Durch die Auswahl dieses Elements die gleiche XAML-Datei dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **Aktivitätsbibliothek** Vorlage für ein neues Projekt. Weitere Informationen zu diesem Verfahren finden Sie unter [Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek](../workflow-designer/how-to-create-an-activity-library.md).|
|Aktivitätsdesigner|Ein Designer, mit dem die Behandlung einer Aktivität zur Entwurfszeit angepasst wird. Durch die Auswahl dieses Elements die gleichen Dateien, die dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **Aktivitätsdesignerbibliothek** Vorlage für ein neues Projekt. Weitere Informationen zu diesem Verfahren finden Sie unter [Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Codeaktivität|Eine Aktivität mit in Code geschriebener Ausführungslogik. Eine Quellcodedatei mit einer Überschreibung der <xref:System.Activities.CodeActivity.Execute%2A>-Methode wird bereits für Sie generiert.|
|WCF-Workflowdienst|Ein [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]-Dienst, der mithilfe von Workflowaktivitäten erstellt wurde. Durch die Auswahl dieses Elements die gleichen Dateien, die dem Projekt hinzugefügt, die Sie erhalten würden, bei der Auswahl der **WCF-Workflowdienstanwendung** Vorlage für ein neues Projekt. Weitere Informationen über diese Prozedur finden Sie unter [Vorgehensweise: Erstellen einer Dienstanwendung für WCF-Workflow](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>So fügen Sie ein neues Element zu einem Workflowprojekt hinzu

1.  Auf der **Projekt** Menü klicken Sie auf **neues Element hinzufügen...** .

     Die **Hinzufügen eines neuen Elements** Dialogfeld wird geöffnet.

2.  In der **installierte Vorlagen** klicken Sie im Bereich **Workflow** Gruppe.

3.  Wählen Sie eines der vier Elemente aus. In der vorherigen Tabelle ist die verfügbare Auswahl aufgeführt.

4.  Geben Sie einen geeigneten Namen für das Element in der **Namen** Feld am unteren Rand des Dialogfelds.

5.  Klicken Sie auf **hinzufügen** um das Element dem aktuellen Workflowprojekt hinzuzufügen.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
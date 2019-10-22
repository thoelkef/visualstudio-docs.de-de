---
title: 'Vorgehensweise: Hinzufügen eines neuen Elements zu einem Workflow Projekt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656634"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Gewusst wie: Hinzufügen eines neuen Elements zu einem Workflowprojekt
Nach der Erstellung eines Workflowprojekts können Sie diesem Projekt Workflowaktivitäten, Designer und andere bekannte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Elemente hinzufügen.

 In der folgenden Tabelle werden die [!INCLUDE[wf](../includes/wf-md.md)]-Elemente aufgeführt, die Sie einem Workflowprojekt hinzufügen können.

|-Name|Beschreibung|
|----------|-----------------|
|Aktivität|Eine Aktivität, die aus anderen Aktivitäten besteht. Wenn Sie dieses Element auswählen, wird dem Projekt die gleiche XAML-Datei hinzugefügt wie beim Auswählen der Vorlage **Aktivitäts Bibliothek** für ein neues Projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] zu diesem Verfahren finden Sie unter Gewusst [wie: Erstellen einer Aktivitäts Bibliothek](../workflow-designer/how-to-create-an-activity-library.md).|
|Aktivitätsdesigner|Ein Designer, mit dem die Behandlung einer Aktivität zur Entwurfszeit angepasst wird. Durch die Auswahl dieses Elements werden dem Projekt die gleichen Dateien hinzugefügt wie beim Auswählen der Vorlage **Aktivitäts Designer Bibliothek** für ein neues Projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] zu diesem Verfahren finden Sie unter Gewusst [wie: Erstellen einer Aktivitäts Designer Bibliothek](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Codeaktivität|Eine Aktivität mit in Code geschriebener Ausführungslogik. Eine Quellcodedatei mit einer Überschreibung der <xref:System.Activities.CodeActivity.Execute%2A>-Methode wird bereits für Sie generiert.|
|WCF-Workflowdienst|Ein [!INCLUDE[indigo2](../includes/indigo2-md.md)]-Dienst, der mithilfe von Workflowaktivitäten erstellt wurde. Durch die Auswahl dieses Elements werden dem Projekt die gleichen Dateien hinzugefügt wie beim Auswählen der Vorlage **WCF-Workflow Dienst Anwendung** für ein neues Projekt. [!INCLUDE[crabout](../includes/crabout-md.md)] zu diesem Verfahren finden Sie unter Gewusst [wie: Erstellen einer WCF-Workflow Dienst Anwendung](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>So fügen Sie ein neues Element zu einem Workflowprojekt hinzu

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen...** .

     Das Dialogfeld **Neues Element hinzufügen** wird geöffnet.

2. Wählen Sie im Bereich **installierte Vorlagen** die Option **Workflow** Gruppe aus.

3. Wählen Sie eines der vier Elemente aus. In der vorherigen Tabelle ist die verfügbare Auswahl aufgeführt.

4. Geben Sie unten im Dialogfeld im Feld **Name** einen passenden Namen für das Element ein.

5. Klicken Sie auf **Hinzufügen** , um das Element dem aktuellen Workflow Projekt hinzuzufügen.

## <a name="see-also"></a>Siehe auch
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
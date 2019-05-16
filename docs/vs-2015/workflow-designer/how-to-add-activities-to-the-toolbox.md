---
title: 'Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0aa6a76555a18c142acb8759b1bc71d56e9d7dcd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690942"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox
Aktivitäten können hinzugefügt werden, um die **Toolbox** in der Projektmappe auf verschiedene Weise. Sie können sie innerhalb des aktuellen Projekts hinzufügen oder durch einen Verweis auf ein anderes Projekt oder eine andere Assembly.  
  
### <a name="to-add-an-activity-from-within-your-current-project"></a>So fügen Sie innerhalb des aktuellen Projekts eine Aktivität hinzu  
  
1. Fügen Sie dem aktuellen Workflowprojekt eine neue benutzerdefinierte Aktivität hinzu. [!INCLUDE[crabout](../includes/crabout-md.md)] Hinzufügen einer neuen benutzerdefinierten Aktivität zu Ihrem Projekt finden Sie unter [Vorgehensweise: Hinzufügen eines neuen Elements zu einem Workflowprojekt](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).  
  
2. Fügen Sie der Aktivität benutzerdefinierte Logik hinzu.  
  
3. Erstellen Sie das Projekt. Wenn der Build erfolgreich war, eine neue Kategorie in der **Toolbox** mit dem Namen "\<*Projektname*>" mit die benutzerdefinierte Aktivität enthält, die in dieser Kategorie wird angezeigt.  
  
    > [!NOTE]
    > Wenn die Toolbox zurückgesetzt wird, werden benutzerdefinierte Aktivitäten entfernt. Dies gilt auch, wenn die Projektmappe erneut erstellt wird. Um die Toolbox erneut mit benutzerdefinierten Aktivitäten aufzufüllen, nachdem sie zurückgesetzt wurde, starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)] erneut.  
  
    > [!NOTE]
    > Die Toolbox kann nur eine Aktivität mit einem bestimmten Namen anzeigen. Wenn zwei Aktivitäten aus verschiedenen Assemblys denselben Klassennamen haben, wird nur eine anzeigt.  
  
    > [!NOTE]
    > Die Anwendungsdomäne wird von Editorinstanzen gemeinsam verwendet. Wenn statische Variablen verwendet werden, werden sie von den Editorinstanzen auch gemeinsam verwendet. Wenn dieses Verhalten nicht erwünscht ist, sollte ein Dienst verwendet werden, um Variableninstanzen nachzuverfolgen. Finden Sie unter [unter Verwendung des Kontexts für die ModelItem-Bearbeitung](https://msdn.microsoft.com/library/7f9f1ea5-0147-4079-8eca-be94f00d3aa1) Informationen zur Verwendung von Diensten innerhalb des Designers.  
  
### <a name="to-add-an-activity-from-within-a-different-project"></a>So fügen eine Aktivität aus einem anderen Projekt hinzu  
  
1. Öffnen Sie eine Projektmappe, die mindestens ein Workflowprojekt und entweder ein benutzerdefiniertes Aktivitätsbibliotheksprojekt oder ein anderes Workflowprojekt enthält, in dem eine benutzerdefinierte Aktivität definiert wird.  
  
2. Erstellen Sie beide Projekte. Wenn die Erstellung erfolgreich war, eine neue Kategorie in der **Toolbox** mit dem Namen "\<*Projektname*>" mit die benutzerdefinierte Aktivität enthält, die in dieser Kategorie wird angezeigt.  
  
### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>So fügen Sie eine Aktivität aus einer Assembly der Toolbox hinzu  
  
1. Öffnen Sie eine Workflowprojektmappe.  
  
2. Von der **Tools** , wählen Sie im Menü **Toolboxelemente auswählen...** .  
  
3. In der **Toolboxelemente** wählen Sie im Dialogfeld die **System.Activities-Komponenten** Registerkarte, und klicken Sie auf **durchsuchen...** Navigieren Sie auf die Assembly, die die benutzerdefinierte Aktivität enthält, die Sie hinzufügen möchten.  
  
4. Wählen Sie die Assembly, und klicken Sie auf **OK**. Die benutzerdefinierte Aktivitätskomponente wird der Liste der Komponenten hinzugefügt und automatisch ausgewählt.  
  
    1. Klicken Sie auf **OK** um das Dialogfeld zu schließen.  
  
5. Wählen Sie zum Anzeigen der Toolbox **Toolbox** aus der **Ansicht** Menü.  
  
6. Die benutzerdefinierte Aktivität wird in der **Toolbox** unter der Kategorie, die im Fokus war, bevor das Element hinzugefügt wurde. Z. B. wenn die **allgemeine** Kategorie ausgewählt wurde, der **Toolbox** vor dem Hinzufügen des Toolboxelements muss die Aktivität wird angezeigt, unter der **allgemeine** Kategorie.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des Workflow-Designers](../workflow-designer/using-the-workflow-designer.md)
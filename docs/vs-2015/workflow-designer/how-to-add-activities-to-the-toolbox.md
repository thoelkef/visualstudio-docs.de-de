---
title: 'Gewusst wie: Hinzufügen von Aktivitäten zur Toolbox | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8fc2af704ab587480913c51cdbc593e6cc0f483a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663465"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Gewusst wie: Hinzufügen von Aktivitäten zur Toolbox
Aktivitäten können auf verschiedene Arten der **Toolbox** in der Projekt Mappe hinzugefügt werden. Sie können sie innerhalb des aktuellen Projekts hinzufügen oder durch einen Verweis auf ein anderes Projekt oder eine andere Assembly.

### <a name="to-add-an-activity-from-within-your-current-project"></a>So fügen Sie innerhalb des aktuellen Projekts eine Aktivität hinzu

1. Fügen Sie dem aktuellen Workflowprojekt eine neue benutzerdefinierte Aktivität hinzu. [!INCLUDE[crabout](../includes/crabout-md.md)] zum Hinzufügen einer neuen benutzerdefinierten Aktivität zum Projekt finden Sie unter Gewusst [wie: Hinzufügen eines neuen Elements zu einem Workflow Projekt](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Fügen Sie der Aktivität benutzerdefinierte Logik hinzu.

3. Erstellen Sie das Projekt. Wenn der Buildvorgang erfolgreich war, wird eine neue Kategorie mit dem Namen "" in der **Toolbox** \<*project name*> mit der benutzerdefinierten Aktivität angezeigt, die in dieser Kategorie enthalten ist.

    > [!NOTE]
    > Wenn die Toolbox zurückgesetzt wird, werden benutzerdefinierte Aktivitäten entfernt. Dies gilt auch, wenn die Projektmappe erneut erstellt wird. Um die Toolbox erneut mit benutzerdefinierten Aktivitäten aufzufüllen, nachdem sie zurückgesetzt wurde, starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)] erneut.

    > [!NOTE]
    > Die Toolbox kann nur eine Aktivität mit einem bestimmten Namen anzeigen. Wenn zwei Aktivitäten aus verschiedenen Assemblys denselben Klassennamen haben, wird nur eine anzeigt.

    > [!NOTE]
    > Die Anwendungsdomäne wird von Editorinstanzen gemeinsam verwendet. Wenn statische Variablen verwendet werden, werden sie von den Editorinstanzen auch gemeinsam verwendet. Wenn dieses Verhalten nicht erwünscht ist, sollte ein Dienst verwendet werden, um Variableninstanzen nachzuverfolgen. Informationen zur Verwendung von Diensten innerhalb des Designers finden [Sie unter Verwenden des Kontext Bearbeitungskontexts](https://msdn.microsoft.com/library/7f9f1ea5-0147-4079-8eca-be94f00d3aa1) .

### <a name="to-add-an-activity-from-within-a-different-project"></a>So fügen eine Aktivität aus einem anderen Projekt hinzu

1. Öffnen Sie eine Projektmappe, die mindestens ein Workflowprojekt und entweder ein benutzerdefiniertes Aktivitätsbibliotheksprojekt oder ein anderes Workflowprojekt enthält, in dem eine benutzerdefinierte Aktivität definiert wird.

2. Erstellen Sie beide Projekte. Wenn die Builds erfolgreich waren, wird eine neue Kategorie mit dem Namen "" in der **Toolbox** \<*project name*> mit der benutzerdefinierten Aktivität angezeigt, die in dieser Kategorie enthalten ist.

### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>So fügen Sie eine Aktivität aus einer Assembly der Toolbox hinzu

1. Öffnen Sie eine Workflowprojektmappe.

2. Wählen Sie **im Menü** Extras die Option **Toolbox Elemente auswählen...** aus.

3. Wählen Sie im Dialogfeld **Toolbox Elemente auswählen** die Registerkarte **System. Activities-Komponenten** aus, und klicken Sie dann auf **Durchsuchen...** zum Navigieren zu der Assembly, die die benutzerdefinierte Aktivität enthält, die Sie hinzufügen möchten.

4. Wählen Sie die Assembly aus, und klicken Sie auf **OK**. Die benutzerdefinierte Aktivitätskomponente wird der Liste der Komponenten hinzugefügt und automatisch ausgewählt.

    1. Klicken Sie auf **OK**, um das Dialogfeld zu schließen.

5. Um die Toolbox anzuzeigen, wählen Sie im Menü **Ansicht** die Option **Toolbox** aus.

6. Die benutzerdefinierte Aktivität wird in der **Toolbox** unter der Kategorie angezeigt, die sich vor dem Hinzufügen des Elements im Fokus befand. Wenn z. b. die Kategorie **Allgemein** in der **Toolbox** vor dem Hinzufügen des Toolbox Elements ausgewählt wurde, wird die Aktivität unter der Kategorie **Allgemein** angezeigt.

## <a name="see-also"></a>Weitere Informationen
 [Verwenden des Workflow-Designers](../workflow-designer/using-the-workflow-designer.md)
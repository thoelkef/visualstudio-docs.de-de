---
title: "Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 275917a56d451c35093bcb1b42aadcb599a4aa4e
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Gewusst wie: Hinzufügen von Aktivitäten zur Toolbox

Aktivitäten können hinzugefügt werden, um die **Toolbox** in der Projektmappe auf verschiedene Weise. Sie können sie innerhalb des aktuellen Projekts hinzufügen oder durch einen Verweis auf ein anderes Projekt oder eine andere Assembly.

## <a name="to-add-an-activity-from-within-your-current-project"></a>So fügen Sie innerhalb des aktuellen Projekts eine Aktivität hinzu

1.  Fügen Sie dem aktuellen Workflowprojekt eine neue benutzerdefinierte Aktivität hinzu. Weitere Informationen zu Ihrem Projekt eine neue benutzerdefinierte Aktivität hinzufügen, finden Sie unter [wie: Hinzufügen eines neuen Elements zu einem Workflowprojekt](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2.  Fügen Sie der Aktivität benutzerdefinierte Logik hinzu.

3.  Erstellen Sie das Projekt. Wenn die Erstellung erfolgreich war, eine neue Kategorie in den **Toolbox** mit dem Namen "\<*Projektname*>" mit die benutzerdefinierte Aktivität enthält, die in dieser Kategorie wird angezeigt.

    > [!NOTE]
    > Wenn die Toolbox zurückgesetzt wird, werden benutzerdefinierte Aktivitäten entfernt. Dies gilt auch, wenn die Projektmappe erneut erstellt wird. Um die Toolbox erneut mit benutzerdefinierten Aktivitäten aufzufüllen, nachdem sie zurückgesetzt wurde, starten Sie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] erneut.

    > [!NOTE]
    > Die Toolbox kann nur eine Aktivität mit einem bestimmten Namen anzeigen. Wenn zwei Aktivitäten aus verschiedenen Assemblys denselben Klassennamen haben, wird nur eine anzeigt.

    > [!NOTE]
    > Die Anwendungsdomäne wird von Editorinstanzen gemeinsam verwendet. Wenn statische Variablen verwendet werden, werden sie von den Editorinstanzen auch gemeinsam verwendet. Wenn dieses Verhalten nicht erwünscht ist, sollte ein Dienst verwendet werden, um Variableninstanzen nachzuverfolgen. Finden Sie unter [unter Verwendung des ModelItem-Kontexts bearbeiten](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) Informationen zum Verwenden von Diensten im Designer.

## <a name="to-add-an-activity-from-within-a-different-project"></a>So fügen eine Aktivität aus einem anderen Projekt hinzu

1.  Öffnen Sie eine Projektmappe, die mindestens ein Workflowprojekt und entweder ein benutzerdefiniertes Aktivitätsbibliotheksprojekt oder ein anderes Workflowprojekt enthält, in dem eine benutzerdefinierte Aktivität definiert wird.

2.  Erstellen Sie beide Projekte. Wenn die Builds erfolgreich waren eine neue Kategorie in den **Toolbox** mit dem Namen "\<*Projektname*>" mit die benutzerdefinierte Aktivität enthält, die in dieser Kategorie wird angezeigt.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>So fügen Sie eine Aktivität aus einer Assembly der Toolbox hinzu

1.  Öffnen Sie eine Workflowprojektmappe.

2.  Aus der **Tools** klicken Sie im Menü **Toolboxelemente auswählen...** .

3.  In der **Toolboxelemente** wählen Sie im Dialogfeld die **System.Activities-Komponenten** Registerkarte, und klicken Sie auf **durchsuchen...**  , auf die Assembly, die die benutzerdefinierte Aktivität enthält, navigieren Sie hinzufügen möchten.

4.  Wählen Sie die Assembly, und klicken Sie auf **OK**. Die benutzerdefinierte Aktivitätskomponente wird der Liste der Komponenten hinzugefügt und automatisch ausgewählt.

    1.  Klicken Sie auf **OK** um das Dialogfeld zu schließen.

5.  Um die Toolbox anzuzeigen, wählen Sie **Toolbox** aus der **Ansicht** Menü.

6.  Die benutzerdefinierte Aktivität wird in der **Toolbox** unter der Kategorie, die im Fokus war, bevor das Element hinzugefügt wurde. Z. B. wenn die **allgemeine** Kategorie ausgewählt wurde, der **Toolbox** vor dem Hinzufügen des Toolboxelements an, der Aktivität angezeigt, unter der **allgemeine** Kategorie.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Workflow-Designers](../workflow-designer/using-the-workflow-designer.md)
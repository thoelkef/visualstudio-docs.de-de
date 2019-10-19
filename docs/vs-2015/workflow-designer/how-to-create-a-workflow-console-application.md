---
title: 'Vorgehensweise: Erstellen einer Konsolenanwendung für Workflows | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604918"
---
# <a name="how-to-create-a-workflow-console-application"></a>Vorgehensweise: Erstellen einer Konsolenanwendung für Workflows
Mit [!INCLUDE[wf](../includes/wf-md.md)] können Sie Workflows zum Ausführen von Systemprozessen oder menschlichen Prozessen erstellen. Der [!INCLUDE[wfd1](../includes/wfd1-md.md)] stellt die Entwurfsoberfläche zum Erstellen dieser Workflows bereit. Der [!INCLUDE[wfd2](../includes/wfd2-md.md)] kann verwendet werden, um Workflows in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zu erstellen, oder er kann in andere Anwendungen integriert werden, die den Designer neu hosten.

 In diesem Thema wird beschrieben, wie der [!INCLUDE[wfd2](../includes/wfd2-md.md)] in [!INCLUDE[vs2010](../includes/vs2010-md.md)] verwendet wird, um einen Workflow in einer Konsolenanwendung zu erstellen.

### <a name="to-create-a-workflow-console-application"></a>So erstellen Sie eine Konsolenanwendung für Workflows

1. Starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Zeigen Sie im Menü **Datei** auf **neu**, und wählen Sie dann **Projekt...** aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie im Bereich **installierte Vorlagen** die Option **Workflow** aus den  **C# Visualisierungs** -oder **Visual Basic** Gruppierungen aus, abhängig von der bevorzugten Sprache.

4. Wählen Sie im mittleren Bereich **Workflow Konsolenanwendung**aus.

5. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

6. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

7. Geben Sie **im Feldprojekt Mappe den Namen** für die neue Projekt Mappe ein. Klicken Sie auf **OK** , um die Anwendung zu erstellen.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projekt Mappe eine Workflow Konsolenanwendung hinzufügen möchten, öffnen Sie diese Projekt Mappe in [!INCLUDE[vs2010](../includes/vs2010-md.md)], klicken Sie mit der rechten Maustaste auf die Projekt Mappe in **Projektmappen-Explorer**, und wählen Sie **Hinzufügen**und dann **Neues Projekt... aus.** , um das Dialogfeld **Neues Projekt** zu öffnen. Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8. Die Projektvorlage erstellt eine Workflowdefinition in XAML, und die Konsolenanwendungsdefinition ist in Quellcode. Der [!INCLUDE[wfd2](../includes/wfd2-md.md)] wird geöffnet und zeigt den Canvas für den Workflow an, den Sie erstellt haben.

9. Um einen Workflow zu erstellen, ziehen Sie Aktivitäten oder andere Workflow Elemente aus der **Toolbox** auf die Entwurfs Oberfläche im Workflow.

## <a name="see-also"></a>Siehe auch
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
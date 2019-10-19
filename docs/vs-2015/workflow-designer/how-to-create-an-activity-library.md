---
title: 'Vorgehensweise: Erstellen einer Aktivitäts Bibliothek | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662758"
---
# <a name="how-to-create-an-activity-library"></a>Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek
Benutzerdefinierte Aktivitäten werden verwendet, um bestimmte Geschäftsprozesse in einem Workflow zu modellieren. Die Vorlage Aktivitätsbibliothek in [!INCLUDE[vs2010](../includes/vs2010-md.md)] wurde bereitgestellt, damit Sie solche benutzerdefinierten Aktivitäten visuell mithilfe von [!INCLUDE[wfd1](../includes/wfd1-md.md)] erstellen können.

### <a name="to-create-a-workflow-activity-library"></a>So erstellen Sie eine Workflowaktivitätsbibliothek

1. Starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Zeigen Sie im Menü **Datei** auf **neu**, und wählen Sie dann **Projekt...** aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie im Bereich **Projekttypen** die Option **Workflow** aus den **visuellen C#**  Projekten oder **Visual Basic** Gruppierungen abhängig von ihrer bevorzugte Sprache aus.

4. Wählen Sie im Bereich **Vorlagen** die Option **Aktivitäts Bibliothek**aus.

5. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

6. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

7. Geben Sie **im Feldprojekt** Mappe einen beschreibenden Namen für die Projekt Mappe ein, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projekt Mappe eine Workflow Konsolenanwendung hinzufügen möchten, öffnen Sie diese Projekt Mappe in [!INCLUDE[vs2010](../includes/vs2010-md.md)], klicken Sie mit der rechten Maustaste auf die Projekt Mappe in **Projektmappen-Explorer**, und wählen Sie **Hinzufügen**und dann **Neues Projekt... aus.** , um das Dialogfeld **Neues Projekt** zu öffnen. Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8. Die Projektvorlage erstellt eine Aktivitätsdefinition im XAML-Format. [!INCLUDE[wfd1](../includes/wfd1-md.md)] wird geöffnet und zeigt den Zeichenbereich für die benutzerdefinierte Aktivität an.

9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfs Oberfläche, um Sie in die benutzerdefinierte Aktivität einzubeziehen.

    > [!CAUTION]
    > Sie können nur eine untergeordnete Aktivität dem Text der benutzerdefinierten Aktivität hinzufügen. Diese untergeordnete Aktivität kann jedoch eine zusammengesetzte Aktivität sein, z. B. eine <xref:System.Activities.Statements.Sequence>-Aktivität oder <xref:System.Activities.Statements.Flowchart>-Aktivität.

## <a name="see-also"></a>Siehe auch
 Vorgehens [Weise: Erstellen einer Aktivität erstellen](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [eines Workflow Projekts](../workflow-designer/creating-a-workflow-project.md)
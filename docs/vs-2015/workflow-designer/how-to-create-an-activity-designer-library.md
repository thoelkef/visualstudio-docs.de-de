---
title: 'Vorgehensweise: Erstellen einer Aktivitäts Designer Bibliothek | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662874"
---
# <a name="how-to-create-an-activity-designer-library"></a>Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek
Mit benutzerdefinierten Aktivitätsdesignern können Sie für eine benutzerdefinierte Aktivität oder eine Standardaktivität eine Benutzeroberfläche erstellen. Sie steuern die Komplexität der Benutzeroberfläche und sind in der Lage, mehrere Aktivitätsdesigner für eine Aktivität zu erstellen. Dieses Szenario ermöglicht es Ihnen, Designer zu erstellen, die auf unterschiedliche Zielgruppen zugeschnitten sind.

### <a name="to-create-an-activity-designer-library"></a>So erstellen Sie eine Aktivitätsdesignerbibliothek

1. Starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Zeigen Sie im Menü **Datei** auf **neu**, und wählen Sie dann **Projekt...** aus. , um das Dialogfeld **Neues Projekt** zu öffnen.

3. Wählen Sie im Bereich **Projekttypen** die Option **Workflow** aus den **Visual c#** -oder **Visual Basic** Gruppierungen abhängig von Ihrer bevorzugten Sprache aus.

4. Wählen Sie im Bereich **Vorlagen** die Option **Aktivitäts Designer Bibliothek**aus.

5. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

6. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

7. Geben Sie **im Feldprojekt** Mappe einen beschreibenden Namen für die Projekt Mappe ein, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projekt Mappe eine Workflow Konsolenanwendung hinzufügen möchten, öffnen Sie diese Projekt Mappe in [!INCLUDE[vs2010](../includes/vs2010-md.md)] , klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Projekt Mappe, und wählen Sie **Hinzufügen**und dann **Neues Projekt...** aus. , um das Dialogfeld **Neues Projekt** zu öffnen. Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8. Die Projektvorlage erstellt eine Aktivitätsdesignerdefinition in XAML und die Code-Behind-Implementierungsdatei im Quellcode. Der [!INCLUDE[wfd1](../includes/wfd1-md.md)] wird geöffnet und zeigt den Canvas für den Aktivitätsdesigner an.

9. Ziehen [!INCLUDE[avalon1](../includes/avalon1-md.md)] Sie Steuerelemente aus der **Toolbox** auf die Entwurfs Oberfläche, um Sie im benutzerdefinierten Aktivitäts Designer zu verwenden.  Ein Beispiel für das Implementieren eines benutzerdefinierten Aktivitäts Designers finden Sie unter Gewusst [wie: Erstellen eines benutzerdefinierten Aktivitäts Designers](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).

    > [!WARNING]
    > Benutzerdefinierte Aktivitäts Designer können für benutzerdefinierte Aktivitäten sowie für Standardaktivitäten verwendet werden [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

## <a name="see-also"></a>Weitere Informationen
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
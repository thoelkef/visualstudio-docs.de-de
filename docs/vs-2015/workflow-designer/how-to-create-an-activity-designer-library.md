---
title: 'Vorgehensweise: Erstellen eine Aktivitätsdesignerbibliothek | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a51b4cdb67590b908bc406b78c04ddf0c5aa3e2f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694559"
---
# <a name="how-to-create-an-activity-designer-library"></a>Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek
Mit benutzerdefinierten Aktivitätsdesignern können Sie für eine benutzerdefinierte Aktivität oder eine Standardaktivität eine Benutzeroberfläche erstellen. Sie steuern die Komplexität der Benutzeroberfläche und sind in der Lage, mehrere Aktivitätsdesigner für eine Aktivität zu erstellen. Dieses Szenario ermöglicht es Ihnen, Designer zu erstellen, die auf unterschiedliche Zielgruppen zugeschnitten sind.  
  
### <a name="to-create-an-activity-designer-library"></a>So erstellen Sie eine Aktivitätsdesignerbibliothek  
  
1. Starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Auf der **Datei** Startmenü **neu**, und wählen Sie dann **Projekt...** zum Öffnen der **neues Projekt** Dialogfeld.  
  
3. In der **Projekttypen** wählen Sie im Bereich **Workflow** entweder die **Visual C#-** oder **Visual Basic** Gruppierungen abhängig von Ihrer bevorzugten die Sprache.  
  
4. In der **Vorlagen** wählen Sie im Bereich **Aktivitäts-Designerbibliothek**.  
  
5. In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.  
  
6. In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt speichern, oder klicken Sie auf möchten **Durchsuchen** dorthin navigieren.  
  
7. In der **Lösung** , geben Sie einen beschreibenden Namen für die Projektmappe, und klicken Sie dann **OK**.  
  
    > [!NOTE]
    > Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in [!INCLUDE[vs2010](../includes/vs2010-md.md)], klicken Sie mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, und klicken Sie dann **Neues Projekt...** zum Öffnen der **neues Projekt** Dialogfeld. Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8. Die Projektvorlage erstellt eine Aktivitätsdesignerdefinition in XAML und die Code-Behind-Implementierungsdatei im Quellcode. Der [!INCLUDE[wfd1](../includes/wfd1-md.md)] wird geöffnet und zeigt den Canvas für den Aktivitätsdesigner an.  
  
9. Ziehen Sie [!INCLUDE[avalon1](../includes/avalon1-md.md)] -Steuerelemente aus der **Toolbox** auf die Entwurfsoberfläche, um sie in Ihrer benutzerdefinierten Aktivitäts-Designer verwenden.  Ein Beispiel zum Implementieren eines benutzerdefinierten Aktivitätsdesigners finden Sie unter [Vorgehensweise: Erstellen ein benutzerdefinierten Aktivitätsdesigners](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).  
  
    > [!WARNING]
    > Benutzerdefinierte Aktivitätsdesigner können verwendet werden, für benutzerdefinierte Aktivitäten sowie Standard- [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]Aktivitäten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
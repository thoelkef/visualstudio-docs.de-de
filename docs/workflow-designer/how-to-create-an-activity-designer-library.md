---
title: "Vorgehensweise: erstellen eine Aktivitätsdesignerbibliothek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84f483c4e280dbf5c1dc303805028456cd1ff59e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-an-activity-designer-library"></a>Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek
Mit benutzerdefinierten Aktivitätsdesignern können Sie für eine benutzerdefinierte Aktivität oder eine Standardaktivität eine Benutzeroberfläche erstellen. Sie steuern die Komplexität der Benutzeroberfläche und sind in der Lage, mehrere Aktivitätsdesigner für eine Aktivität zu erstellen. Dieses Szenario ermöglicht es Ihnen, Designer zu erstellen, die auf unterschiedliche Zielgruppen zugeschnitten sind.  
  
### <a name="to-create-an-activity-designer-library"></a>So erstellen Sie eine Aktivitätsdesignerbibliothek  
  
1.  Starten Sie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Auf der **Datei** Sie im Menü **neu**, und wählen Sie dann **Projekt...**  So öffnen die **neues Projekt** (Dialogfeld).  
  
3.  In der **Projekttypen** klicken Sie im Bereich **Workflow** entweder aus der **Visual C#-** oder **Visual Basic** Gruppierungen je nach Ihrer bevorzugten Sprache.  
  
4.  In der **Vorlagen** klicken Sie im Bereich **Aktivitätsdesignerbibliothek**.  
  
5.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.  
  
6.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.  
  
7.  In der **Lösung** Feld, geben Sie einen beschreibenden Namen für die Projektmappe, und klicken Sie auf **OK**.  
  
    > [!NOTE]
    >  Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], klicken Sie mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, dann **Neues Projekt...**  So öffnen die **neues Projekt** (Dialogfeld). Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8.  Die Projektvorlage erstellt eine Aktivitätsdesignerdefinition in XAML und die Code-Behind-Implementierungsdatei im Quellcode. Der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] wird geöffnet und zeigt den Canvas für den Aktivitätsdesigner an.  
  
9. Ziehen Sie [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] -Steuerelemente aus der **Toolbox** auf die Entwurfsoberfläche, um sie im benutzerdefinierten Aktivitätsdesigner zu verwenden.  Ein Beispiel zum Implementieren eines benutzerdefinierten Aktivitätsdesigners, finden Sie unter [Vorgehensweise: Erstellen eines benutzerdefinierten Aktivitätsdesigners](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).  
  
    > [!WARNING]
    >  Benutzerdefinierte Aktivitätsdesigner können verwendet werden, für die benutzerdefinierte Aktivitäten sowie Standard- [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]Aktivitäten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
---
title: "Vorgehensweise: Erstellen einer Aktivit&#228;tsdesignerbibliothek | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Erstellen einer Aktivit&#228;tsdesignerbibliothek
Mit benutzerdefinierten Aktivitätsdesignern können Sie für eine benutzerdefinierte Aktivität oder eine Standardaktivität eine Benutzeroberfläche erstellen.Sie steuern die Komplexität der Benutzeroberfläche und sind in der Lage, mehrere Aktivitätsdesigner für eine Aktivität zu erstellen.Dieses Szenario ermöglicht es Ihnen, Designer zu erstellen, die auf unterschiedliche Zielgruppen zugeschnitten sind.  
  
### So erstellen Sie eine Aktivitätsdesignerbibliothek  
  
1.  Starten Sie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und wählen Sie dann  **Neues Projekt**, um das Dialogfeld **Neues Projekt** zu öffnen.  
  
3.  Wählen Sie im Bereich **Projekttypen** die Option **Workflow** aus der **Visual C\#**\- oder **Visual Basic**\-Gruppe aus, abhängig von der bevorzugten Sprache.  
  
4.  Wählen Sie im Bereich **Vorlagen** die Option **Aktivitätsdesignerbibliothek** aus.  
  
5.  Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, um es einfach identifizieren zu können.  
  
6.  Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem das Projekt gespeichert werden soll, oder klicken Sie auf **Durchsuchen**, um zu dem Verzeichnis zu navigieren.  
  
7.  Geben Sie im Feld **Projektmappe** einen aussagekräftigen Namen für die Projektmappe ein, klicken Sie dann auf **OK**.  
  
    > [!NOTE]
    >  Wenn Sie einer vorhandenen Projektmappe eine Workflowkonsolenanwendung hinzufügen möchten, öffnen Sie diese Projektmappe in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], klicken Sie mit der rechten Maustaste im **Projektmappen\-Explorer** auf die Projektmappe, und wählen Sie **Hinzufügen** und dann **Neues Projekt** aus, um das Dialogfeld **Neues Projekt** zu öffnen.Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8.  Die Projektvorlage erstellt eine Aktivitätsdesignerdefinition in XAML und die Code\-Behind\-Implementierungsdatei im Quellcode.Der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] wird geöffnet und zeigt den Canvas für den Aktivitätsdesigner an.  
  
9. Ziehen Sie [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]\-Steuerelemente aus der **Toolbox** in die Entwurfsoberfläche, um sie im benutzerdefinierten Aktivitätsdesigner zu verwenden.Ein Beispiel für das Implementieren eines benutzerdefinierten Aktivitätsdesigners finden Sie unter [Vorgehensweise: Erstellen eines benutzerdefinierten Aktivitätsdesigners](../Topic/How%20to:%20Create%20a%20Custom%20Activity%20Designer.md).  
  
    > [!WARNING]
    >  Benutzerdefinierte Aktivitätsdesigner können für benutzerdefinierte Aktivitäten sowie Standard\-[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]\-Aktivitäten verwendet werden.  
  
## Siehe auch  
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)
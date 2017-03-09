---
title: "Dialogfeld &quot;Steuerelementbindung anpassen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datauicustomization"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Steuerelementbindung anpassen (Dialogfeld)"
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Dialogfeld &quot;Steuerelementbindung anpassen&quot;
Verwenden Sie das Dialogfeld **Steuerelementbindung anpassen**, um anzugeben, welche Steuerelemente für Elemente im [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) verfügbar sind.  
  
 Jedem Element im **Datenquellenfenster** ist eine Liste von Steuerelementen zugeordnet, die an das Element gebunden werden können.  Die für jedes Element verfügbaren Steuerelemente werden vom Datentyp des Elements bestimmt.  Jedem Datentyp ist eine Liste gültiger Steuerelemente zugeordnet, die in diesem Dialogfeld definiert werden, einschließlich eines Standardsteuerelements.  
  
 Bevor Sie ein Element auf eine Entwurfsoberfläche ziehen, um ein datengebundenes Steuerelement zu erstellen, können Sie auswählen, welches Steuerelement erstellt werden soll.  Wenn Sie ein Element aus dem **Datenquellenfenster** auf eine Entwurfsoberfläche ziehen, ohne ein Steuerelement auszuwählen, wird der Entwurfsoberfläche das Standardsteuerelement für den Datentyp des ausgewählten Elements hinzugefügt.  
  
 Weitere Informationen über das Verwenden dieses Dialogfelds zum Anpassen der Liste von Steuerelementen für Elemente im **Datenquellenfenster** finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## UIElement-Liste  
 **Datentyp**  
 Zeigt eine Liste der Typen an, die Sie Steuerelementen zuordnen:  
  
-   Tabellen, Entitäten und Objekte werden als Elemente vom Typ **\[Liste\]** dargestellt.  
  
-   Spalten oder öffentliche Eigenschaften von Entitäten und Objekten werden im zugrunde liegenden Datenspeicher als der eigentliche Datentyp der Spalte bzw. Eigenschaft dargestellt.  
  
-   Objekte mit benutzerdefinierten Formen werden als **\[Other\]** dargestellt.  Wenn die Anwendung z. B. ein benutzerdefiniertes Steuerelement enthält, das Daten von mehreren Objekteigenschaften anzeigt, wählen Sie für das Steuerelement den Datentyp **\[Andere\]** aus.  
  
 **Zugeordnete Steuerelemente**  
 Zeigt eine Liste der Steuerelemente an, die Sie einem bestimmten Datentyp zuordnen können.  Wenn Sie dem in der Liste **Datentyp** ausgewählten Datentyp ein bestimmtes Steuerelement zuordnen möchten, aktivieren Sie das entsprechende Kontrollkästchen.  Deaktivieren Sie das Kontrollkästchen, um eine Assoziation zu entfernen.  Aktivierte Steuerelemente werden im Kontextmenü angezeigt, das im **Datenquellenfenster** für ein Element des zugeordneten Datentyps aufgerufen wird.  
  
 Sie können der Liste Steuerelemente hinzufügen, indem Sie der **Toolbox** Steuerelemente hinzufügen, die über eines von mehreren Datenbindungsattributen verfügen.  Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Standardwert festlegen**  
 Weist Elementen des ausgewählten Datentyps den ausgewählten Steuerelementtyp als Standard zu.  Das Standardsteuerelement wird als erste Auswahl im Kontextmenü angezeigt, das im **Datenquellenfenster** für ein Element aufgerufen wird.  Es kann nur ein Steuerelementtyp einem Datentyp als Standard zugewiesen werden.  
  
 **Standardwert löschen**  
 Entfernt die Bezeichnung eines Steuerelements als Standard für den ausgewählten Datentyp.  Wenn dem ausgewählten Datentyp kein Standard zugewiesen wurde, wird als erste Auswahl **\[Keine\]** im Kontextmenü angezeigt, das im **Datenquellenfenster** für ein Element des zugeordneten Typs aufgerufen wird.  
  
## Siehe auch  
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
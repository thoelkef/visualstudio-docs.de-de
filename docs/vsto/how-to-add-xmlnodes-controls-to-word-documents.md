---
title: "Gewusst wie: Hinzuf&#252;gen von XMLNodes-Steuerelementen zu Word-Dokumenten"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Dokumenten"
  - "XMLNodes-Steuerelement, Hinzufügen zu Dokumenten"
ms.assetid: 315c6def-51f6-4ba6-bd9e-55cdf70f15bf
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Gewusst wie: Hinzuf&#252;gen von XMLNodes-Steuerelementen zu Word-Dokumenten
  **Wichtig** die Informationen, die in diesem Thema bezüglich Microsoft Word erläutert werden, wird ausschließlich für den Nutzen und die Verwendung von Personen und Organisationen, die außerhalb der USA und ihrer Außengebiete befinden, oder die verwenden, oder entwickeln Programme, die auf ausgeführt werden, Microsoft Word\-Produkte dargestellt, die von Microsoft vor Januar 2010 lizenziert wurden, als Microsoft eine Implementierung der bestimmte Funktionen Beziehung zur benutzerdefinierten XML aus Microsoft Word entfernt wurde.  Diese Informationen bezüglich Microsoft Word dürfen nicht von Personen oder Organisationen in den Vereinigten Staaten oder ihren Außengebieten verwendet werden, die Programme verwenden oder entwickeln, die unter Microsoft Word\-Produkten ausgeführt werden, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden. Diese Produkte verhalten sich nicht wie Produkte, die vor diesem Datum lizenziert oder für die Verwendung außerhalb der Vereinigten Staaten erworben und lizenziert wurden.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Wenn Sie einem Microsoft Office Word\-Dokument ein sich wiederholendes XML\-Schemaelement zuordnen, fügt Visual Studio dem Dokument automatisch ein <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement hinzu.  
  
 Informationen über das Zuordnen sich nicht wiederholender XML\-Schemaelemente finden Sie unter [Gewusst wie: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Das <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement ist weder über die **Toolbox** noch über das **Datenquellenfenster** verfügbar. Auch programmgesteuert kann es nicht erstellt werden.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### So fügen Sie einem Dokument ein XMLNodes\-Steuerelement hinzu  
  
1.  Klicken Sie im Dokument im Visual Studio\-Designer im Menüband auf die Registerkarte **Entwickler**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  Klicken Sie in der Gruppe **XML** auf **Schema**.  
  
     Das Dialogfeld **Vorlagen und Add\-Ins** wird geöffnet.  
  
3.  Klicken Sie auf die Registerkarte **XML\-Schema**.  
  
4.  Klicken Sie auf **Schema hinzufügen**.  
  
     Das Dialogfeld **Schema hinzufügen** wird geöffnet.  
  
5.  Wählen Sie ein XML\-Schema aus, das sich wiederholende Schemaelemente enthält, und klicken Sie auf **Öffnen**.  
  
     Das Dialogfeld **Schemaeinstellungen** wird angezeigt.  
  
6.  Weisen Sie einen Alias zu, oder klicken Sie auf **OK**, um das Schema ohne einen Alias hinzuzufügen.  
  
     Dem Dialogfeld **Schema hinzufügen** wird das Schema hinzugefügt.  
  
7.  Klicken Sie im Dialogfeld **Schema hinzufügen** auf **OK**.  
  
     Der Aufgabenbereich **XML\-Struktur** wird geöffnet.  
  
8.  Klicken Sie im Aufgabenbereich **XML\-Struktur** auf das wiederholende Schemaelement, um es dem Dokument hinzuzufügen.  
  
     Es wird ein <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement erstellt und dem Projekt hinzugefügt.  
  
## Siehe auch  
 [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  
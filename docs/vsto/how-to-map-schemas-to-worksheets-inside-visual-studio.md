---
title: "Gewusst wie: Zuordnen von Schemas zu Arbeitsbl&#228;ttern in Visual Studio | Microsoft Docs"
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
  - "Excel [Office-Entwicklung in Visual Studio], XML-Schemas"
  - "Zuordnungen [Office-Entwicklung in Visual Studio], XML-Schemas zu Excel-Arbeitsblättern"
  - "Arbeitsblätter [Office-Entwicklung in Visual Studio], XML-Schemas"
  - "XML-Schemas [Office-Entwicklung in Visual Studio], Zuordnen"
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Gewusst wie: Zuordnen von Schemas zu Arbeitsbl&#228;ttern in Visual Studio
  Sie können einem Arbeitsblatt ein XML\-Schema zuordnen, während das Arbeitsblatt in Visual Studio geöffnet ist  Sie verwenden dieselben Microsoft Office Excel\-Tools, die Sie verwenden, wenn die Arbeitsmappe außerhalb von Visual Studio geöffnet ist.  Es spielt keine Rolle, ob Sie das Schema vor oder nach dem Erstellen der Excel\-Projektmappe dem Arbeitsblatt zuordnen. Das Office\-Projekt erstellt in beiden Fällen die gleichen Objekte.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  In Excel\-Projektmappen können keine mehrteiligen XML\-Schemas verwendet werden.  
  
### So ordnen Sie einem Excel\-Arbeitsblatt in Visual Studio ein XML\-Schema zu  
  
1.  Öffnen Sie die Excel\-Arbeitsmappe oder das Vorlagenprojekt in Visual Studio.  
  
2.  Klicken Sie im Arbeitsblatt, um den Fokus in den Designer zu verschieben.  
  
3.  Klicken Sie im Menüband auf die Registerkarte **Entwickler**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Klicken Sie in der Gruppe **XML** auf **Quelle**.  
  
     Das Fenster **XML\-Quelle** wird geöffnet.  
  
5.  Klicken Sie im Fenster **XML\-Quelle** auf **XML\-Zuordnungen**.  
  
     Das Dialogfeld **XML\-Verknüpfungen** wird geöffnet.  
  
6.  Klicken Sie im Dialogfeld **XML\-Zuordnungen** auf die Schaltfläche **Hinzufügen**.  
  
7.  Wechseln Sie zur Schemadatei, wählen Sie sie aus, und klicken Sie auf **Öffnen**.  
  
8.  Klicken Sie auf **OK**.  
  
     Das Schema wird im Fenster **XML\-Quelle** dargestellt.  In Ihrem Projekt wird ein typisierter <xref:System.Data.DataSet> auf Grundlage des Schemas generiert und eine <xref:System.Windows.Forms.BindingSource> erstellt.  
  
9. Ziehen Sie Elemente vom Fenster **XML\-Quelle** an die Stellen des Arbeitsblatts, an dem die entsprechenden Steuerelemente erstellt werden sollen.  
  
     Wenn Sie ein sich nicht wiederholendes Schemaelement ziehen, generiert das Office\-Projekt ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement, das automatisch zu <xref:System.Windows.Forms.BindingSource> gebunden ist.  
  
     Wenn Sie ein sich wiederholendes Schemaelement ziehen, generiert das Office\-Projekt ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement, das nicht automatisch an eine Datenquelle gebunden wird.  Weitere Informationen finden Sie unter [XML-Schemas und -Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## Siehe auch  
 [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [XML-Schemas und -Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  
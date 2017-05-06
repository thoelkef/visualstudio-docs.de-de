---
title: "Arbeitsblatthostelement"
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
  - "Hostelemente [Office-Entwicklung in Visual Studio], Worksheet"
  - "Excel [Office-Entwicklung in Visual Studio], Arbeitsblätter"
  - "Arbeitsblatt-Hostelemente"
  - "Arbeitsblätter, Ereignisse"
  - "Worksheet-Hostelemente, Ereignisse"
  - "Excel-Arbeitsblätter"
  - "Arbeitsblätter, Excel"
  - "Arbeitsblätter"
  - "Ereignisse [Office-Entwicklung in Visual Studio]"
ms.assetid: b4f7c501-81f5-409e-aa1b-748f010798b9
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Arbeitsblatthostelement
  Das <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement ist ein Typ, der den <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Typ aus der primären Interopassembly für Excel erweitert. Das <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement stellt die gleichen Eigenschaften, Methoden und Ereignisse wie ein <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt bereit, es macht jedoch auch zusätzliche Ereignisse verfügbar und fungiert als Container für Hoststeuerelemente und Windows Forms\-Steuerelemente.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 In Projekten auf Dokumentebene können Sie <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelemente einem Projekt zur Entwurfszeit hinzufügen. In VSTO\-Add\-In\-Projekten können Sie <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelemente zur Laufzeit generieren.  
  
## Grundlegendes zu Worksheet\-Hostelementen in Projekten auf Dokumentebene  
 Wenn Sie ein Projekt auf Dokumentebene für Excel erstellen, werden von Visual Studio automatisch drei <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelemente im Projekt erstellt. Die Standardnamen der Arbeitsblätter sind `Sheet1`, `Sheet2` und `Sheet3`. Wenn Sie ein Projekt auf Basis einer vorhandenen Arbeitsmappe erstellen, wird die Anzahl von Hostelementen von der Anzahl von Arbeitsblättern in der Arbeitsmappe bestimmt.  
  
 Über diese Arbeitsblattklassen erhalten Sie Zugriff auf Member des <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelements, um grundlegende Aufgaben in Ihrer Anpassung auszuführen, beispielsweise das Ändern des Inhalts eines Arbeitsblatts. Sie können diese Klassen auch verwenden, um den Arbeitsblättern Steuerelemente hinzuzufügen. Sie können Steuerelemente an Daten binden, Benutzerinformationen abfragen und auf Benutzeraktionen reagieren, indem Sie verschiedene Gruppen von Steuerelementen kombinieren und Code schreiben. Weitere Informationen finden Sie unter [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
 Die Arbeitsblattklassen stellen einen Ausgangspunkt bereit, an dem Sie mit dem Schreiben von Code im Projekt beginnen können. Da die Klassen die gleichen Eigenschaften, Methoden und Ereignisse wie das <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt in der primären Interopassembly für Excel bereitstellen, können Sie über diese Klassen auch auf das Objektmodell von Excel zugreifen. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).  
  
 In Projekten auf Dokumentebene können Sie dem Projekt zur Entwurfszeit weitere <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelemente hinzufügen, indem Sie der Arbeitsmappe im Designer ein neues Arbeitsblatt hinzufügen.  
  
### Umbenennen von Arbeitsblättern  
 In einem Projekt auf Dokumentebene können die Arbeitsblätter im Visual Studio\-Designer umbenannt werden, wodurch jedoch nur der Anzeigename des Arbeitsblatts geändert wird. Der Name im Programm ist weiterhin der Standardname des Arbeitsblatts. Wenn Sie das Arbeitsblatt im Fenster **Eigenschaften** umbenennen, wird nur der Name im Programm geändert.  
  
### Einschränkungen des Worksheet\-Hostelements in Projekten auf Dokumentebene  
 In einem Projekt auf Dokumentebene können Sie zur Laufzeit keine neuen <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelemente erstellen. Wenn Sie zur Laufzeit ein neues Excel\-Arbeitsblatt erstellen, hat es den Typ <xref:Microsoft.Office.Interop.Excel.Worksheet>. Da das Arbeitsblatt kein Hostelement ist, kann es keine Hoststeuerelemente bzw. Windows Forms\-Steuerelemente enthalten. Weitere Informationen über das Erstellen von Dokumenten zur Laufzeit finden Sie unter [Gewusst wie: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
## Grundlegendes zu Worksheet\-Hostelementen in VSTO\-Add\-In\-Projekten  
 In Projekten auf Anwendungsebene können Sie für jedes Arbeitsblatt, das in Excel geöffnet ist, zur Laufzeit ein <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement erstellen. Sie können das <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement verwenden, um dem zugeordneten Arbeitsblatt Steuerelemente hinzuzufügen, oder um Ereignisse zu behandeln, die für <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekte nicht verfügbar sind.  
  
 Verwenden Sie zum Generieren eines <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelements die GetVstoObject\-Methode. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Siehe auch  
 [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  
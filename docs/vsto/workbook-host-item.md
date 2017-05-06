---
title: "Arbeitsmappenhostelement"
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
  - "Excel-Arbeitsmappen"
  - "Arbeitsmappen-Hostelemente"
  - "Hostelemente [Office-Entwicklung in Visual Studio], Arbeitsmappe"
  - "Arbeitsmappen, Excel"
  - "Arbeitsmappen-Hostelemente, Ereignisse"
  - "Arbeitsmappen"
  - "Excel [Office-Entwicklung in Visual Studio], Arbeitsmappen"
  - "Arbeitsmappen, Ereignisse"
  - "Ereignisse [Office-Entwicklung in Visual Studio]"
ms.assetid: 54489d91-a799-4dc2-89b8-498cf17c2f57
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Arbeitsmappenhostelement
  Das <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelement ist ein Typ, der den <xref:Microsoft.Office.Interop.Excel.Workbook>\-Typ aus der primären Interopassembly für Excel erweitert. Das <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelement stellt die gleichen Eigenschaften, Methoden und Ereignisse wie ein <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekt bereit, bietet jedoch auch zusätzliche Funktionen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 In Projekten auf Dokumentebene gibt es ein <xref:Microsoft.Office.Tools.Excel.Workbook>\-Standardhostelement, das die Arbeitsmappe im Projekt darstellt. In VSTO\-Add\-In\-Projekten können Sie <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelemente zur Laufzeit generieren.  
  
## Grundlegendes zum Arbeitsmappen\-Hostelement in Projekten auf Dokumentebene  
 Verwenden Sie die `ThisWorkbook`\-Klasse, um auf die Arbeitsmappe im Projekt zuzugreifen. Über die `ThisWorkbook`\-Klasse erhalten Sie Zugriff auf Member des <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelements, um grundlegende Aufgaben in der Anpassung auszuführen, z. B. das Ausführen von Code, wenn die Arbeitsmappe geöffnet bzw. geschlossen wird. Weitere Informationen finden Sie unter [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
 Die `ThisWorkbook`\-Klasse stellt einen Ausgangspunkt bereit, an dem Sie mit dem Schreiben von Code im Projekt beginnen können. Da die Klasse die gleichen Eigenschaften, Methoden und Ereignisse wie das <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekt in der primären Interopassembly für Excel bereitstellt, können Sie auch mit `ThisWorkbook` auf das Excel\-Objektmodell zugreifen. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).  
  
 Doppelklicken Sie im **Projektmappen\-Explorer** auf das **ThisWorkbook**\-Projektelement, um den Arbeitsmappen\-Designer und die Eigenschaften und Ereignisse der Arbeitsmappe im Fenster **Eigenschaften** anzuzeigen.  
  
### Einschränkungen des Arbeitsmappen\-Hostelements in Projekten auf Dokumentebene  
 Ein Projekt auf Dokumentebene kann nur ein <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelement \(die `ThisWorkbook`\-Klasse\) enthalten. Sie können dem Projekt zur Entwurfszeit keine neuen <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelemente hinzufügen, und Sie können zur Laufzeit von einer Anpassung auf Dokumentebene keine neuen <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelemente erstellen.  
  
 Wenn Sie zur Laufzeit eine neue Excel\-Arbeitsmappe erstellen, hat sie den Typ <xref:Microsoft.Office.Interop.Excel.Workbook>. Da es kein Hostelement ist, kann es keine Hoststeuerelemente bzw. Windows Forms\-Steuerelemente enthalten. Weitere Informationen über das Erstellen von Arbeitsmappen zur Laufzeit finden Sie unter [Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
 Das <xref:Microsoft.Office.Tools.Excel.Workbook> Hostelement dient nicht als Container für Hoststeuerelemente. Daher können Sie der Arbeitsmappe keine sichtbaren Steuerelemente hinzufügen. Sie können jedoch Komponenten wie <xref:System.Data.DataSet> hinzufügen, sodass die Komponenten von allen Arbeitsblättern gemeinsam genutzt werden können. In einem Projekt auf Dokumentebene befinden sich die für die Arbeitsmappe verfügbare Komponenten auf den Registerkarten **Komponente**, **Daten** und **Alle Windows Forms** der **Toolbox**.  
  
> [!NOTE]  
>  Die Office\-Entwicklungstools in Visual Studio unterstützen keine freigegebenen Arbeitsmappen.  
  
## Grundlegendes zu Arbeitsmappen\-Hostelementen in VSTO\-Add\-In\-Projekten  
 In VSTO\-Add\-In\-Projekten können Sie für jede Arbeitsmappe, die in Excel geöffnet ist, zur Laufzeit ein <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelement generieren. Verwenden Sie zum Generieren eines <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelements die GetVstoObject\-Methode. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Siehe auch  
 [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  
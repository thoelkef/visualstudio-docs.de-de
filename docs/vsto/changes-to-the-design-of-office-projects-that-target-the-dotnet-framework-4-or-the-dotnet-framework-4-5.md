---
title: "&#196;nderungen am Entwurf von Office-Projekten, die auf .NET Framework&#160;4 oder .NET Framework 4.5 abzielen | Microsoft Docs"
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
  - "Office-Entwicklung in Visual Studio, Neuigkeiten"
  - "Neuigkeiten [Office-Entwicklung in Visual Studio]"
ms.assetid: 290f5cb4-e2ee-4ed8-987c-2f013405cee9
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# &#196;nderungen am Entwurf von Office-Projekten, die auf .NET Framework&#160;4 oder .NET Framework 4.5 abzielen
  Mit [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] wurden in Visual Studio einige Änderungen am Entwurf von Office\-Projekten eingeführt, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielen. Wenn Sie mit Office\-Projekten in früheren Versionen von Visual Studio vertraut sind, sollten Sie diese Änderungen beachten, bevor Sie Office\-Projekte entwickeln, die für diese Versionen von .NET Framework 4.0 oder höher bestimmt sind. Standardmäßig zielen alle Projekte, die Sie mit Visual Studio 2013 oder höher erstellen, auf .NET Framework 4.0 oder höher ab.  
  
 In den folgenden Abschnitten werden diese Office\-Projektentwurfänderungen beschrieben.  
  
## Grundlegendes zum neuen schnittstellenbasierten Entwurf der Visual Studio 2010\-Tools für Office\-Laufzeit  
 Wenn Sie ein Office\-Projekt entwickeln, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielt, sind die meisten Typen, die Sie in Visual Studio 2010\-Tools für Office\-Laufzeit verwenden, Schnittstellen. Dies ist eine wesentliche Änderung im Vergleich zu früheren Versionen der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], in denen diese Typen Klassen sind. Wenn Sie z. B. auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielen, sind der <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Typ und der <xref:Microsoft.Office.Tools.Word.Document>\-Typ Schnittstellen statt Klassen. Weitere Informationen finden Sie unter [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 Bei Typen, die Sie in früheren Versionen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] direkt instanziieren konnten, rufen Sie jetzt Instanzen dieser Typen mithilfe von Methoden des Globals.Factory\-Objekts ab. Verwenden Sie z. B. die <xref:Microsoft.Office.Tools.Excel.SmartTag>\-Methode, um ein Objekt abzurufen, das die Globals.Factory.CreateSmartTag\-Schnittstelle implementiert. Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Aktualisieren von Excel- und Word-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren der Anpassungen von Menübändern in Office-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren von Formularbereichen in Outlook-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### Neue Basisklassen in Office\-Projekten  
 Der neue schnittstellenbasierte Entwurf von Visual Studio 2010\-Tools für Office\-Laufzeit beeinflusst die erstellten Klassen in Office\-Projekten, wie `ThisDocument`, `ThisWorkbook` und `ThisAddIn`. In Office\-Projekten, die auf .NET Framework 3.5 und frühere Versionen des Frameworks abzielen, werden diese erstellten Klassen von Klassen in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] abgeleitet, z. B. Microsoft.Office.Tools.Word.Document, Microsoft.Office.Tools.Excel.Worksheet und Microsoft.Office.Tools.AddIn. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielen, sind diese [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]\-Klassen jetzt Schnittstellen. Daher können die erstellten Klassen in Office\-Projekten nicht mehr ihre Implementierung von ihnen ableiten. Stattdessen werden die erstellten Klassen von neuen Basisklassen wie <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase> und <xref:Microsoft.Office.Tools.AddInBase> abgeleitet. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md) und [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
 Die Basisklassen sind nicht Teil der verteilbaren [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Stattdessen werden sie in Hilfsprogrammassemblys definiert, die in Visual Studio enthalten sind. Diese Assemblys werden beim Erstellen von Office\-Projekten in den Ausgabeordner kopiert und müssen mit der Lösung bereitgestellt werden. Weitere Informationen zu den Hilfsprogrammassemblys finden Sie unter [Assemblys in Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## Unterbrechende Änderungen in Office\-Projekten, für die .NET Framework 4 als Zielversion neu zugewiesen wird  
 In der folgenden Tabelle sind die wichtigsten unterbrechenden Änderungen für Office\-Projekte aufgeführt, denen [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher als Zielversion neu zugewiesen wird. Weitere Details finden Sie unter [Migrieren von Office-Projektmappen in .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Unterbrechende Änderung|Auswirkung|  
|-----------------------------|----------------|  
|Das <xref:System.Security.SecurityTransparentAttribute> wird in Office\-Projekten nicht mehr verwendet oder unterstützt.|Sie müssen dieses Attribut aus der AssemblyInfo\-Codedatei in Office\-Projekten entfernen, die Sie von Visual Studio 2008 aktualisieren. Weitere Informationen finden Sie unter [Erforderliche Änderungen zum Ausführen von Office-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Das ExcelLocale1033Attribute wird in Excel\-Projekten nicht mehr verwendet oder unterstützt.|Sie müssen dieses Attribut aus der AssemblyInfo\-Codedatei in Excel\-Projekten entfernen. Weitere Informationen finden Sie unter [Aktualisieren von Excel- und Word-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Das Programmiermodell von **Menüband \(Visueller Designer\)**\-Projektelementen hat sich geändert.|Sie müssen die CodeBehind\-Datei für alle Menübandelemente im Projekt ändern. Sie müssen außerdem Code ändern, in dem Menüband\-Steuerelemente zur Laufzeit instanziiert werden, Menübandereignisse behandelt werden oder die Position einer Menübandkomponente programmgesteuert festgelegt wird. Weitere Informationen finden Sie unter [Aktualisieren der Anpassungen von Menübändern in Office-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Das Programmiermodell von Outlook\-Formularbereichen hat sich geändert.|Sie müssen die CodeBehind\-Datei für alle Formularbereiche im Projekt und für Code ändern, in dem bestimmte Formularbereichklassen zur Laufzeit instanziiert werden. Weitere Informationen finden Sie unter [Aktualisieren von Formularbereichen in Outlook-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Das Programmiermodell für Smarttags in Excel\- und Word\-Projekte hat sich geändert. Smarttags sind in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] veraltet.|Wenn die Projektmappe Smarttags verwendet, treten beim Erstellen des Projekts Fehler auf. Da Smarttags in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] veraltet sind, müssen Sie die Tags entfernen, bevor Sie die Projektmappe in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] oder höher testen und debuggen können.|  
|Die Syntax der GetVstoObject\- und HasVstoObject\-Methoden wurde geändert.|Sie müssen das Globals.Factory\-Objekt an diese Methoden übergeben, wenn Sie in systemeigenen Objekten aus den primären Interopassemblys \(PIAs\) auf sie zugreifen, oder Sie können auf diese Methoden in dem Objekt zugreifen, das von der Globals.Factory\-Eigenschaft im Projekt zurückgegeben wird. Weitere Informationen finden Sie unter [Aktualisieren von Excel- und Word-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Die Ereignisse von Word\-Inhaltssteuerelementen sind neuen Delegaten zugeordnet.|Sie müssen Code ändern, in dem Ereignisse von Word\-Inhaltssteuerelementen behandelt werden, um die neuen Delegaten anzugeben. Weitere Informationen finden Sie unter [Aktualisieren von Excel- und Word-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Die OLEObject\-Klasse und die OLEControl\-Klasse wurden umbenannt.|Sie müssen Code ändern, in dem Instanzen dieser Klassen verwendet werden, um stattdessen das <xref:Microsoft.Office.Tools.Excel.ControlSite>\-Objekt oder <xref:Microsoft.Office.Tools.Word.ControlSite>\-Objekt zu verwenden. Weitere Informationen finden Sie unter [Aktualisieren von Excel- und Word-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Hostelementklassen, wie `ThisWorkbook`, `Sheet`*n*, `ThisDocument` und `ThisAddIn`, stellen keine Dispose\-Methode mehr bereit, die überschrieben werden kann.|Sie müssen den Code in der Dispose\-Methodenüberschreibung in den Shutdown\-Ereignishandler in der Hostelementklasse, z. B. `ThisAddIn_Shutdown`, verschieben und die Dispose\-Methodenüberschreibung aus der Hostelementklasse entfernen.|  
  
## Siehe auch  
 [Migrieren von Office-Projektmappen in .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Neuigkeiten bei der Office\-Entwicklung](http://msdn.microsoft.com/de-de/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  
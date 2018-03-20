---
title: "Änderungen am Entwurf von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 abzielen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 059d259b669e63c26759782010be7ff78691ffc3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Änderungen am Entwurf von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 abzielen
  Mit [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]wurden in Visual Studio einige Änderungen am Entwurf von Office-Projekten eingeführt, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielen. Wenn Sie mit Office-Projekten in früheren Versionen von Visual Studio vertraut sind, sollten Sie diese Änderungen beachten, bevor Sie Office-Projekte entwickeln, die für diese Versionen von .NET Framework 4.0 oder höher bestimmt sind. Standardmäßig zielen alle Projekte, die Sie mit Visual Studio 2013 oder höher erstellen, auf .NET Framework 4.0 oder höher ab.  
  
 In den folgenden Abschnitten werden diese Office-Projektentwurfänderungen beschrieben.  
  
## <a name="understanding-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Grundlegendes zum neuen schnittstellenbasierten Entwurf der Visual Studio 2010-Tools für Office-Laufzeit  
 Wenn Sie ein Office-Projekt entwickeln, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielt, sind die meisten Typen, die Sie in Visual Studio 2010-Tools für Office-Laufzeit verwenden, Schnittstellen. Dies ist eine wesentliche Änderung im Vergleich zu früheren Versionen der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], in denen diese Typen Klassen sind. Wenn Sie z. B. auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielen, sind der <xref:Microsoft.Office.Tools.Excel.Worksheet> -Typ und der <xref:Microsoft.Office.Tools.Word.Document> -Typ Schnittstellen statt Klassen. Weitere Informationen finden Sie unter [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 Für alle Typen, die Sie in früheren Versionen von direkt instanziieren konnten die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], Sie Methoden des Objekts Globals.Factory jetzt zum Abrufen von Instanzen dieser Typen verwenden. Beispielsweise, um ein Objekt abzurufen, implementiert die <xref:Microsoft.Office.Tools.Excel.SmartTag> -Schnittstelle, die Globals.Factory.CreateSmartTag-Methode verwenden. Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Aktualisieren von Excel- und Word-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren von Menübändern in Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualisieren von Formularbereichen in Outlook-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Neue Basisklassen in Office-Projekten  
 Der neue schnittstellenbasierte Entwurf von Visual Studio 2010-Tools für Office-Laufzeit beeinflusst die erstellten Klassen in Office-Projekten, wie `ThisDocument`, `ThisWorkbook`und `ThisAddIn`. In Office-Projekten, die .NET Framework 3.5 und frühere Versionen des Frameworks abzielen, leiten Sie diese erstellten Klassen von Klassen in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] z. B. Microsoft.Office.Tools.Word.Document Microsoft.Office.Tools.Excel.Worksheet, und Microsoft.Office.Tools.AddIn. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielen, sind diese [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] -Klassen jetzt Schnittstellen. Daher können die erstellten Klassen in Office-Projekten nicht mehr ihre Implementierung von ihnen ableiten. Stattdessen werden die erstellten Klassen von neuen Basisklassen wie <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>und <xref:Microsoft.Office.Tools.AddInBase>abgeleitet. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md) und [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 Die Basisklassen sind nicht Teil der verteilbaren [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Stattdessen werden sie in Hilfsprogrammassemblys definiert, die in Visual Studio enthalten sind. Diese Assemblys werden beim Erstellen von Office-Projekten in den Ausgabeordner kopiert und müssen mit der Lösung bereitgestellt werden. Weitere Informationen zu den Hilfsprogrammassemblys finden Sie unter [Assemblies in the Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Unterbrechende Änderungen in Office-Projekten, für die .NET Framework 4 als Zielversion neu zugewiesen wird  
 In der folgenden Tabelle sind die wichtigsten unterbrechenden Änderungen für Office-Projekte aufgeführt, denen [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher als Zielversion neu zugewiesen wird. Weitere Informationen finden Sie unter [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Unterbrechende Änderung|Auswirkung|  
|---------------------|-----------------|  
|Das <xref:System.Security.SecurityTransparentAttribute> wird in Office-Projekten nicht mehr verwendet oder unterstützt.|Sie müssen dieses Attribut aus der AssemblyInfo-Codedatei in Office-Projekten entfernen, die Sie von Visual Studio 2008 aktualisieren. Weitere Informationen finden Sie unter [Änderungen erforderlich sind, führen Sie Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Das ExcelLocale1033Attribute wird nicht mehr verwendet oder in Excel-Projekten unterstützt.|Sie müssen dieses Attribut aus der AssemblyInfo-Codedatei in Excel-Projekten entfernen. Weitere Informationen finden Sie unter [Aktualisieren von Excel- und Word-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Das Programmiermodell von **Menüband (Visueller Designer)** -Projektelementen hat sich geändert.|Sie müssen die CodeBehind-Datei für alle Menübandelemente im Projekt ändern. Sie müssen außerdem Code ändern, in dem Menüband-Steuerelemente zur Laufzeit instanziiert werden, Menübandereignisse behandelt werden oder die Position einer Menübandkomponente programmgesteuert festgelegt wird. Weitere Informationen finden Sie unter [Aktualisieren von Menübändern in Office-Projekten, die Sie in .NET Framework 4 oder .NET Framework 4.5 migrieren](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Das Programmiermodell von Outlook-Formularbereichen hat sich geändert.|Sie müssen die CodeBehind-Datei für alle Formularbereiche im Projekt und für Code ändern, in dem bestimmte Formularbereichklassen zur Laufzeit instanziiert werden. Weitere Informationen finden Sie unter [Aktualisieren von Formularbereichen in Outlook-Projekte, die Sie in .NET Framework 4 oder .NET Framework 4.5 migrieren](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Das Programmiermodell für Smarttags in Excel- und Word-Projekte hat sich geändert. Smarttags sind in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]veraltet.|Wenn die Projektmappe Smarttags verwendet, treten beim Erstellen des Projekts Fehler auf. Da Smarttags in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]veraltet sind, müssen Sie die Tags entfernen, bevor Sie die Projektmappe in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] oder höher testen und debuggen können.|  
|Die Syntax der Methoden GetVstoObject und HasVstoObject hat sich geändert.|Wenn Sie in systemeigenen Objekten aus der primären Interop-Assemblys (PIAs) zugreifen oder Sie können diese Methoden für das Objekt, das von der Eigenschaft Globals.Factory im Projekt zurückgegeben wird zugreifen, müssen Sie die Globals.Factory-Objekt an diese Methoden übergeben. Weitere Informationen finden Sie unter [Aktualisieren von Excel- und Word-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Die Ereignisse von Word-Inhaltssteuerelementen sind neuen Delegaten zugeordnet.|Sie müssen Code ändern, in dem Ereignisse von Word-Inhaltssteuerelementen behandelt werden, um die neuen Delegaten anzugeben. Weitere Informationen finden Sie unter [Aktualisieren von Excel- und Word-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Die OLEObject-Klasse und OLEControl-Klasse wurden umbenannt.|Sie müssen Code ändern, in dem Instanzen dieser Klassen verwendet werden, um stattdessen das <xref:Microsoft.Office.Tools.Excel.ControlSite> -Objekt oder <xref:Microsoft.Office.Tools.Word.ControlSite> -Objekt zu verwenden. Weitere Informationen finden Sie unter [Aktualisieren von Excel- und Word-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Hostelementklassen, wie z. B. `ThisWorkbook`, `Sheet`  *n* , `ThisDocument`, und `ThisAddIn`, nicht mehr bieten eine Dispose-Methode, die Sie überschreiben können.|Müssen Sie keinen Code in der Überschreibung der Dispose-Methode auf Verschieben der Shutdown-Ereignishandler in der Hostelementklasse, z. B. `ThisAddIn_Shutdown`, und die Außerkraftsetzung der Dispose-Methode aus der Hostelementklasse entfernen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Neuigkeiten in Office-Entwicklung](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Übersicht über die Visual Studio-Tools für Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  
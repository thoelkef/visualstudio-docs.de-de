---
title: Assemblys in Visual Studio-Tools für Office-Laufzeit | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34ce422757ad7e7f7152920252eff6e0c2277261
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assemblys in Visual Studio Tools for Office Runtime
  Wenn Sie ein Office-Projekt erstellen, fügt Visual Studio automatisch Verweise auf die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] -Assemblys hinzu, die für den Projekttyp und das Ziel-.NET Framework des Projekts verwendet werden. In den Office-Erweiterungen für .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]und [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]sind verschiedene Assemblys vorhanden. Weitere Informationen zu den Office-Erweiterungen finden Sie unter [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Assemblys in den Office-Erweiterungen für .NET Framework 4 und [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 In der folgenden Tabelle sind die Assemblys aufgeführt, die in Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]enthalten sind. Dokumentation zu den Namespaces und Typen in diesen Assemblys finden Sie [Referenz zur verwalteten &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Assemblyname|Beschreibung|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Stellt folgende Typen bereit:<br /><br /> -Typen zum Erstellen von menübandanpassungen und Smarttags. **Hinweis:** Smarttags sind veraltet, im [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Typen zum Erstellen von Aktionsbereichen in Anpassungen auf Dokumentebene und benutzerdefinierten Aufgabenbereichen in VSTO-Add-Ins.|  
|Microsoft.Office.Tools.Excel.dll|Stellt Schnittstellen bereit, die Hostelemente und Hoststeuerelemente für Excel-Projekte und unterstützende Typen darstellen. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Enthält Typen, mit denen Sie benutzerdefinierte Formularbereiche in VSTO-Add-Ins für Outlook erstellen können.|  
|Microsoft.Office.Tools.Word.dll|Stellt Schnittstellen bereit, die Hostelemente und Hoststeuerelemente für Word-Projekte und unterstützende Typen darstellen. Weitere Informationen finden Sie unter [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Stellt folgende Typen bereit:<br /><br /> -Ausnahmen, die von der Visual Studio-Tools für Office-Laufzeit ausgelöst werden können.<br />-Attribute, die Sie, beim Erstellen von Outlook verwenden können-Formularbereichen.|  
|Microsoft.Office.Tools.dll|Stellt Typen bereit, die zur Infrastruktur der Visual Studio-Tools für Office-Laufzeit gehören und nicht für die direkte Verwendung durch den Code vorgesehen sind.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Stellt folgende Typen bereit:<br /><br /> – Der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut und <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Schnittstelle, die zum Zwischenspeichern von Datenobjekten in einer Anpassung auf Dokumentebene verwendet werden können. Weitere Informationen finden Sie unter [Caching Data](../vsto/caching-data.md).<br />– Der <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> -Schnittstelle, die Sie implementieren können, um zusätzliche Installationsschritte als abschließenden Schritt des ClickOnce-Installationsprogramms für eine Office-Projektmappe auszuführen. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Ausnahmen, die von der Visual Studio-Tools für Office-Laufzeit ausgelöst werden können.<br />– Andere Typen, die Teil der Visual Studio-Tools für Office Runtime-Infrastruktur und nicht direkt aus Ihrem Code verwendet werden sollen.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Stellt folgende Typen bereit:<br /><br /> – Der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> -Klasse, die zum Anfügen von Anpassungsassemblys an Dokumente und Zugriff auf die zwischengespeicherten Daten in Dokumenten verwendet werden können. Weitere Informationen finden Sie unter [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Mehrere Klassen, die die Hierarchie der darstellt, zwischengespeicherte Daten in einer Anpassung auf Dokumentebene. Weitere Informationen finden Sie unter [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Projekte, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] abzielen, verweisen auch auf die folgenden Assemblys. Diese Assemblys sind nicht Teil der verteilbaren [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Vielmehr handelt es sich um abhängige Assemblys, die mit Ihrer Lösung bereitgestellt werden müssen. Standardmäßig werden sie in den Ausgabeordner für die Erstellung für das Projekt kopiert (die Eigenschaft **Lokale Kopie** für diese Assemblys wird auf **True**festgelegt). Wenn Sie das Projekt mithilfe von ClickOnce bereitstellen, sind diese Assemblys im generierten Paket enthalten.  
  
|Assemblyname|Beschreibung|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Stellt die Basisklassen für die generierte `ThisAddIn` -Klasse in VSTO-Add-In-Projekten und die generierte Menübandklasse in allen Projekten bereit.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Stellt folgende Typen bereit:<br /><br /> -Basisklassen für die generierte `ThisWorkbook` und `Sheet` Klassen in Dokumentebene Projekte für Excel.<br />-Windows Forms-Steuerelemente, die Sie in Arbeitsblättern in Excel-Projekten verwenden können.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Stellt Basisklassen für die generierten `ThisAddIn` - und Formularbereichsklassen in Outlook-Projekten bereit.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Stellt folgende Typen bereit:<br /><br /> -Basisklassen für die generierte `ThisDocument` -Klasse in Projekten auf Dokumentebene für Word.<br />-Windows Forms-Steuerelemente, die in Dokumenten in Word-Projekten verwendet werden können.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assemblys in den Office-Erweiterungen für .NET Framework 3.5  
 In der folgenden Tabelle sind die Assemblys aufgeführt, die in den Office-Erweiterungen für .NET Framework 3.5. enthalten sind. Dokumentation zu den Namespaces und Klassen in diesen Assemblys finden Sie im folgenden Verweisabschnitt in der Visual Studio 2008-Dokumentation: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Assemblyname|Beschreibung|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die Microsoft.Office.Tools.AddIn Basisklasse für VSTO-Add-Ins.<br />-Klassen zum Erstellen von menübandanpassungen und Smarttags. **Hinweis:** Smarttags sind veraltet, im [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Klassen zum Erstellen von Aktionsbereichen in Anpassungen auf Dokumentebene und benutzerdefinierten Aufgabenbereichen in VSTO-Add-Ins.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Stellt Hostelemente und Hoststeuerelemente für Excel-Lösungen bereit. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Stellt Klassen bereit, mit denen Sie benutzerdefinierte Formularbereiche in Outlook-VSTO-Add-Ins erstellen können.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Stellt Hostelemente und Hoststeuerelemente für Word--Lösungen bereit. Weitere Informationen finden Sie unter [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent-Klasse, die die Datenbindungsfunktionen für Hoststeuerelemente in Anpassungen auf Dokumentebene bereitstellt.<br />– Andere Typen, die Teil der Visual Studio-Tools für Office Runtime-Infrastruktur und nicht direkt aus Ihrem Code verwendet werden sollen.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute-Attribut und Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType-Schnittstelle, die zum Zwischenspeichern von Datenobjekten in einer Anpassung auf Dokumentebene verwendet werden können. Weitere Informationen finden Sie unter [Caching Data](../vsto/caching-data.md).<br />-Ausnahmen, die von der Visual Studio-Tools für Office-Laufzeit ausgelöst werden können.<br />– Andere Typen, die Teil der Visual Studio-Tools für Office Runtime-Infrastruktur und nicht direkt aus Ihrem Code verwendet werden sollen.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Stellt die Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction-Schnittstelle, die Sie implementieren können, um zusätzliche Installationsschritte als abschließenden Schritt des ClickOnce-Installationsprogramms für eine Office-Projektmappe auszuführen. Weitere Informationen finden Sie unter [Advanced Office Solution Deployment](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die Klasse "Microsoft.VisualStudio.Tools.Applications.ServerDocument" hinzu, die zum programmgesteuerten Anfügen von Anpassungsassemblys an Dokumente und Zugriff auf die zwischengespeicherten Daten in Dokumenten verwendet werden können. Weitere Informationen finden Sie unter [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Mehrere Klassen, die die Hierarchie der darstellt, zwischengespeicherte Daten in einer Anpassung auf Dokumentebene. Weitere Informationen finden Sie unter [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry und Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList-Klassen, die Sie verwenden können, zum Erstellen von Listeneinträgen Vertrauenswürdigkeit gewährt werden, um Office Projektmappen, die .NET Framework 3.5 abzielen.<br />– Andere Typen, die Teil der Visual Studio-Tools für Office Runtime-Infrastruktur und nicht direkt aus Ihrem Code verwendet werden sollen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über die Visual Studio-Tools für Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Laufzeitinstallationsszenarios für Visual Studio-Tools für Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  
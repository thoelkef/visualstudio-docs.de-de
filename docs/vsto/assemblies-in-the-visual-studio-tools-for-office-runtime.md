---
title: Assemblys in Visual Studio Tools for Office-Laufzeit
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa7cb056ade43b01d1c9533354a53c9a735dd88f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919013"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assemblys in Visual Studio Tools for Office-Laufzeit
  Wenn Sie ein Office-Projekt erstellen, fügt Visual Studio automatisch Verweise auf die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] -Assemblys hinzu, die für den Projekttyp und das Ziel-.NET Framework des Projekts verwendet werden. In den Office-Erweiterungen für .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]und [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]sind verschiedene Assemblys vorhanden. Weitere Informationen zu den Office-Erweiterungen, finden Sie unter [Visual Studio-Tools für Office-laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Assemblys in Office-Erweiterungen für .NET Framework 4 und [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 In der folgenden Tabelle sind die Assemblys aufgeführt, die in Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]enthalten sind. Dokumentation zu den Namespaces und Typen in diesen Assemblys finden Sie [verwaltete Referenz zu &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Assemblyname|Beschreibung|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Stellt folgende Typen bereit:<br /><br /> -Typen zum Erstellen von menübandanpassungen und Smarttags. **Hinweis**:      Smarttags sind in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]veraltet.<br />-Typen zum Erstellen von Aktionsbereichen in Anpassungen auf Dokumentebene und benutzerdefinierten Aufgabenbereichen in VSTO-Add-Ins.|  
|Microsoft.Office.Tools.Excel.dll|Stellt Schnittstellen bereit, die Hostelemente und Hoststeuerelemente für Excel-Projekte und unterstützende Typen darstellen. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Enthält Typen, mit denen Sie benutzerdefinierte Formularbereiche in VSTO-Add-Ins für Outlook erstellen können.|  
|Microsoft.Office.Tools.Word.dll|Stellt Schnittstellen bereit, die Hostelemente und Hoststeuerelemente für Word-Projekte und unterstützende Typen darstellen. Weitere Informationen finden Sie unter [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Stellt folgende Typen bereit:<br /><br /> -Ausnahmen, die von der Visual Studio-Tools für Office-Laufzeit ausgelöst werden können.<br />-Attribute, mit denen Sie beim Erstellen von Outlook-Formularbereiche.|  
|Microsoft.Office.Tools.dll|Stellt Typen bereit, die zur Infrastruktur der Visual Studio-Tools für Office-Laufzeit gehören und nicht für die direkte Verwendung durch den Code vorgesehen sind.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Stellt folgende Typen bereit:<br /><br /> – Die <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut und <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> -Schnittstelle, die Sie zum Zwischenspeichern von Datenobjekten in einer Anpassung auf Dokumentebene verwenden können. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).<br />– Die <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> -Schnittstelle, die Sie implementieren können, um zusätzliche Installationsschritte als abschließenden Schritt des ClickOnce-Installationsprogramms für eine Office-Projektmappe auszuführen. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Ausnahmen, die von der Visual Studio-Tools für Office-Laufzeit ausgelöst werden können.<br />-Andere Typen, die Teil von Visual Studio-Tools für Office Runtime-Infrastruktur und sollen nicht direkt aus Ihrem Code verwendet werden.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Stellt folgende Typen bereit:<br /><br /> – Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> -Klasse, die Sie zum Anfügen von Anpassungsassemblys an Dokumente und Zugriff auf die zwischengespeicherten Daten in Dokumenten verwenden können. Weitere Informationen finden Sie unter [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Mehrere Klassen, die darstellen, die Hierarchie der zwischengespeicherten Daten in einer Anpassung auf Dokumentebene. Weitere Informationen finden Sie unter [Zugriff auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Projekte, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] abzielen, verweisen auch auf die folgenden Assemblys. Diese Assemblys sind nicht Teil der verteilbaren [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Vielmehr handelt es sich um abhängige Assemblys, die mit Ihrer Lösung bereitgestellt werden müssen. Standardmäßig werden sie in den Ausgabeordner für die Erstellung für das Projekt kopiert (die Eigenschaft **Lokale Kopie** für diese Assemblys wird auf **True**festgelegt). Wenn Sie das Projekt mithilfe von ClickOnce bereitstellen, sind diese Assemblys im generierten Paket enthalten.  
  
|Assemblyname|Beschreibung|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Stellt die Basisklassen für die generierte `ThisAddIn` -Klasse in VSTO-Add-In-Projekten und die generierte Menübandklasse in allen Projekten bereit.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Stellt folgende Typen bereit:<br /><br /> -Basisklassen für die generierte `ThisWorkbook` und `Sheet` Klassen im auf Dokumentebene Projekte für Excel.<br />-Windows Forms-Steuerelemente, die Sie in Arbeitsblättern in Excel-Projekten verwenden können.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Stellt Basisklassen für die generierten `ThisAddIn` - und Formularbereichsklassen in Outlook-Projekten bereit.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Stellt folgende Typen bereit:<br /><br /> -Basisklassen für die generierte `ThisDocument` -Klasse in Projekten auf Dokumentebene für Word.<br />-Windows Forms-Steuerelemente, die Sie in den Dokumenten in Word-Projekten verwenden können.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assemblys in Office-Erweiterungen für .NET Framework 3.5  
 In der folgenden Tabelle sind die Assemblys aufgeführt, die in den Office-Erweiterungen für .NET Framework 3.5. enthalten sind. Dokumentation zu den Namespaces und Klassen in diesen Assemblys finden Sie im folgenden Verweisabschnitt in der Dokumentation zu Visual Studio 2008: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Assemblyname|Beschreibung|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die Microsoft.Office.Tools.AddIn-Basisklasse für VSTO-Add-ins.<br />-Klassen zum Erstellen von menübandanpassungen und Smarttags. **Hinweis**:      Smarttags sind in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]veraltet.<br />-Klassen zum Erstellen von Aktionsbereichen in Anpassungen auf Dokumentebene und benutzerdefinierten Aufgabenbereichen in VSTO-Add-ins.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Stellt Hostelemente und Hoststeuerelemente für Excel-Lösungen bereit. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Stellt Klassen bereit, mit denen Sie benutzerdefinierte Formularbereiche in Outlook-VSTO-Add-Ins erstellen können.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Stellt Hostelemente und Hoststeuerelemente für Word--Lösungen bereit. Weitere Informationen finden Sie unter [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> – Die [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) -Klasse, die die Datenbindungsfunktionen für Hoststeuerelemente in Anpassungen auf Dokumentebene zu bereitstellt.<br />-Andere Typen, die Teil von Visual Studio-Tools für Office Runtime-Infrastruktur und sollen nicht direkt aus Ihrem Code verwendet werden.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> – Die <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut und <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> -Schnittstelle, die Sie zum Zwischenspeichern von Datenobjekten in einer Anpassung auf Dokumentebene verwenden können. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).<br />-Ausnahmen, die von der Visual Studio-Tools für Office-Laufzeit ausgelöst werden können.<br />-Andere Typen, die Teil von Visual Studio-Tools für Office Runtime-Infrastruktur und sollen nicht direkt aus Ihrem Code verwendet werden.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Stellt die <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>-Schnittstelle bereit, die Sie implementieren können, um zusätzliche Installationsschritte als abschließenden Schritt des ClickOnce-Installationsprogramms für eine Office-Lösung auszuführen. Weitere Informationen finden Sie unter [erweiterter Office-projektmappenbereitstellung](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Stellt folgende Typen bereit:<br /><br /> – Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> -Klasse, die Sie zum programmgesteuerten Anfügen von Anpassungsassemblys an Dokumente und Zugriff auf die zwischengespeicherten Daten in Dokumenten verwenden können. Weitere Informationen finden Sie unter [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Mehrere Klassen, die darstellen, die Hierarchie der zwischengespeicherten Daten in einer Anpassung auf Dokumentebene. Weitere Informationen finden Sie unter [Zugriff auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Stellt folgende Typen bereit:<br /><br /> – Die Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry und Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList-Klassen, die Sie verwenden können, zum Erstellen von Vertrauenswürdigkeit für Office zu gewähren Lösungen, die auf .NET Framework 3.5 abzielen.<br />-Andere Typen, die Teil von Visual Studio-Tools für Office Runtime-Infrastruktur und sollen nicht direkt aus Ihrem Code verwendet werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Tools für Office-laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio-Tools für Office Runtime Installation scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  

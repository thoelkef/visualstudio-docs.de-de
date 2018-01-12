---
title: "Primäre Interopassemblys für Office | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 906100a572170f218a23b1887ab7fddee37251b9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="office-primary-interop-assemblies"></a>Primäre Interop-Assemblys in Office
  Zur Verwendung der Funktionen einer Microsoft Office-Anwendung in einem Office-Projekt müssen Sie die primäre Interop-Assembly (PIA) für diese Anwendung verwenden. Die PIA ermöglicht es verwaltetem Code, mit dem COM-basierten Objektmodell einer Microsoft Office-Anwendung zu interagieren.  
  
 Wenn Sie ein neues Office-Projekt erstellen, fügt Visual Studio Verweise auf die PIAs hinzu, die zum Erstellen des Projekts erforderlich sind. In einigen Szenarien müssen Sie Verweise auf zusätzliche PIAs hinzufügen (beispielsweise, wenn Sie eine Funktion von Microsoft Office Word in einem Projekt für Microsoft Office Excel verwenden möchten).  
  
 In diesem Thema werden die folgenden Aspekte der Verwendung von Microsoft Office PIAs in Office-Projekten beschrieben:  
  
-   [Separate primäre Interop-Assemblys zum Erstellen und Ausführen von Projekten](#separateassemblies)  
  
-   [Verwenden von Funktionen mehrerer Microsoft Office-Anwendungen in einem einzelnen Projekt](#usingfeatures)  
  
-   [Vollständige Liste primärer Interop-Assemblys für Microsoft Office-Anwendungen](#pialist)  
  
 Weitere Informationen zu primären Interopassemblys finden Sie unter [Primäre Interop-Assemblys](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).  
  
##  <a name="separateassemblies"></a> Separate Primary Interop Assemblies for Building and Running Projects  
 Visual Studio verwendet unterschiedliche Sätze von PIAs auf dem Entwicklungscomputer. Diese unterschiedlichen Assemblysätze befinden sich an den folgenden Speicherorten:  
  
-   In einem Ordner im Verzeichnis "Programme".  
  
     Diese Kopien der Assemblys werden verwendet, wenn Sie Code schreiben und Projekte erstellen. Visual Studio installiert diese Assemblys automatisch.  
  
-   Im globalen Assemblycache.  
  
     Diese Kopien der Assemblys werden bei einigen Entwicklungsaufgaben verwendet, z. B. wenn Sie Projekte ausführen oder debuggen. Visual Studio installiert und registriert diese Assemblys nicht; Sie müssen dies selbst tun.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Primäre Interop-Assemblys im Verzeichnis "Programme"  
 Bei der Installation von Visual Studio werden die PIAs automatisch an einem Speicherort im Dateisystem außerhalb des globalen Assemblycaches installiert. Wenn Sie ein neues Projekt erstellen, fügt Visual Studio automatisch Verweise auf diese Kopien der PIAs zu Ihrem Projekt hinzu. Visual Studio verwendet diese PIA-Kopien anstelle der Assemblys im globalen Assemblycache, um Typverweise aufzulösen, wenn Sie das Projekt entwickeln und erstellen.  
  
 Diese Kopien der PIAs helfen dabei, mehrere Entwicklungsprobleme im Zusammenhang mit Visual Studio zu vermeiden. Diese können auftreten, wenn unterschiedliche Versionen der PIAs im globalen Assemblycache registriert werden.  
  
 Visual Studio installiert diese Kopien der PIAs an den folgenden Speicherorten auf dem Entwicklungscomputer:  
  
-   %Programme%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office14  
  
     (oder %Programme(x86)%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office14 auf 64-Bit-Betriebssystemen)  
  
-   %Programme%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office15  
  
     (oder %Programme(x86)%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\Office15 auf 64-Bit-Betriebssystemen)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Installieren von primären Interop-Assemblys im globalen Assemblycache  
 Für die Ausführung bestimmter Entwicklungsaufgaben müssen die PIAs im globalen Assemblycache auf dem Entwicklungscomputer installiert und registriert sein. In der Regel werden die PIAs automatisch installiert, wenn Sie Office auf dem Entwicklungscomputer installieren. Weitere Informationen finden Sie unter [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Zur Ausführung von Office-Lösungen sind die Office-PIAs auf Endbenutzercomputern nicht erforderlich. Weitere Informationen finden Sie unter [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
##  <a name="usingfeatures"></a> Using Features of Multiple Microsoft Office Applications in a Single Project  
 Jede Office-Projektvorlage in Visual Studio wird im Hinblick auf die Arbeit mit einer einzelnen Microsoft Office-Anwendung entworfen. Um Funktionen in mehreren Microsoft Office-Anwendungen oder in einer Anwendung bzw. Komponente zu verwenden, die kein Projekt in Visual Studio besitzt, müssen Sie einen Verweis auf die erforderlichen PIAs hinzufügen.  
  
 In den meisten Fällen sollten Sie Verweise auf die primären Interop-Assemblys (PIAs) hinzufügen, die von Visual Studio im Verzeichnis %Programme%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\ installiert werden. Diese Versionen der Assemblys werden im Dialogfeld **Verweis-Manager** auf der Registerkarte **Framework** angezeigt. Weitere Informationen finden Sie unter [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
 Wenn Sie die PIAs im globalen Assemblycache installiert und registriert haben, werden diese Versionen im Dialogfeld **Verweis-Manager** auf der Registerkarte **COM** angezeigt. Vermeiden Sie es, Verweise auf diese Versionen hinzuzufügen, da sonst bei ihrer Verwendung Entwicklungsprobleme auftreten können. Wenn verschiedene Versionen der PIAs im globalen Assemblycache registriert sind, bindet das Projekt automatisch an die Version der Assembly, die zuletzt registriert wurde - auch dann, wenn Sie im Dialogfeld **Verweis-Manager** auf der Registerkarte **COM** eine andere Version angeben.  
  
> [!NOTE]  
>  Einige Assemblys werden einem Projekt automatisch hinzugefügt, wenn eine Assembly hinzugefügt wird, die auf sie verweist. Verweise auf die Assemblys "Office.dll" und "Microsoft.Vbe.Interop.dll" werden beispielsweise automatisch hinzugefügt, wenn Sie einen Verweis auf die Word-, Excel-, Outlook-, Microsoft Forms- oder Graph-Assembly hinzufügen.  
  
##  <a name="pialist"></a> Primäre Interop-Assemblys für Microsoft Office-Anwendungen  
 In der folgenden Tabelle werden die primären Interop-Assemblys aufgelistet, die für [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]verfügbar sind.  
  
|Office-Anwendung oder Office-Komponente|Name der primären Interop-Assembly|  
|-------------------------------------|-----------------------------------|  
|Microsoft Access 14.0-Objektbibliothek<br /><br /> Microsoft Access 15,0-Objektbibliothek|Microsoft.Office.Interop.Access.dll|  
|Objektbibliothek des Microsoft Office 14.0 Access-Datenbankmoduls<br /><br /> Objektbibliothek des Microsoft Office 15,0 Access-Datenbankmoduls|Microsoft.Office.Interop.Access.Dao.dll|  
|Microsoft Excel 14.0-Objektbibliothek<br /><br /> Microsoft Excel 15,0-Objektbibliothek|Microsoft.Office.Interop.Excel.dll|  
|Microsoft Graph 14.0-Objektbibliothek(wird von PowerPoint, Access und Word für Diagramme verwendet)<br /><br /> Microsoft Graph 15.0-Objektbibliothek|Microsoft.Office.Interop.Graph.dll|  
|Microsoft InfoPath 2.0-Typbibliothek (nur für InfoPath 2007)|Microsoft.Office.Interop.InfoPath.dll|  
|Microsoft InfoPath-XML-Interop-Assembly (nur für InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Microsoft Office 14.0-Objektbibliothek (gemeinsam genutzte Office-Funktionen)<br /><br /> Microsoft Office 15,0-Objektbibliothek (gemeinsam genutzte Office-Funktionen)|office.dll|  
|Microsoft Office Outlook-Ansichtssteuerelement (kann auf Webseiten und in Anwendungen für den Zugriff auf den Posteingang verwendet werden)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Microsoft Outlook 14.0-Objektbibliothek<br /><br /> Microsoft Outlook 15,0-Objektbibliothek|Microsoft.Office.Interop.Outlook.dll|  
|Microsoft PowerPoint 14.0-Objektbibliothek<br /><br /> Microsoft PowerPoint 15,0-Objektbibliothek|Microsoft.Office.Interop.PowerPoint.dll|  
|Microsoft Project 14.0-Objektbibliothek<br /><br /> Microsoft Project 15,0-Objektbibliothek|Microsoft.Office.Interop.MSProject.dll|  
|Microsoft Publisher 14.0-Objektbibliothek<br /><br /> Microsoft Publisher 15,0-Objektbibliothek|Microsoft.Office.Interop.Publisher.dll|  
|Microsoft SharePoint Designer 14.0-Webobjekt-Verweisbibliothek|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Microsoft SharePoint Designer 14.0-Seitenobjekt-Verweisbibliothek|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Microsoft Smart Tags 2.0-Typbibliothek **Hinweis:** Smarttags sind veraltet, im [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Microsoft Visio 14.0-Typbibliothek<br /><br /> Microsoft Visio 15,0-Typbibliothek|Microsoft.Office.Interop.Visio.dll|  
|Microsoft Visio 14.0-Typbibliothek für "Speichern als Web"<br /><br /> Microsoft Visio 15,0-Typbibliothek für "Speichern als Web"|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Microsoft Visio 14.0-Typbibliothek für Zeichnungssteuerelemente<br /><br /> Microsoft Visio 15,0-Typbibliothek für Zeichnungssteuerelemente|Microsoft.Office.Interop.VisOcx.dll|  
|Microsoft Word 14.0-Objektbibliothek<br /><br /> Microsoft Word 15,0-Objektbibliothek|Microsoft.Office.Interop.Word.dll|  
|Microsoft Visual Basic for Applications Erweiterung 5.3|Microsoft.Vbe.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Bindungsumleitungsassemblys  
 Wenn Sie die Office-PIAs im globalen Assemblycache installieren und registrieren (entweder mit Office oder durch das Installieren des verteilbaren Pakets für die PIAs), werden die Bindungsumleitungsassemblys ebenfalls nur im globalen Assemblycache installiert. Diese Assemblys tragen dazu bei, dass die richtige Version der primären Interop-Assemblys zur Laufzeit geladen wird. Wenn eine Projektmappe, die auf eine Assembly für [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] verweist, beispielsweise auf einem Computer mit der [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Version derselben primären Interop-Assembly ausgeführt wird, weist die Bindungsumleitungsassembly die [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] -Laufzeit an, die [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Version der primären Interop-Assembly zu laden. Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren und Deaktivieren der Bindungsumleitung](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>Siehe auch  
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)   
 [InfoPath-Lösungen](../vsto/infopath-solutions.md)   
 [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)   
 [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md)   
 [Projektmappen](../vsto/project-solutions.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Allgemeine Referenz &#40; Office-Entwicklung in Visual Studio &#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  
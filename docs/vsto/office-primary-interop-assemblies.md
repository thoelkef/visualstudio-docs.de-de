---
title: Primäre Interop-Assemblys in Office
ms.custom: ''
ms.date: 09/20/2018
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c309dcfd78ae0181905f691e1c36f407e763fc93
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542480"
---
# <a name="office-primary-interop-assemblies"></a>Primäre Interop-Assemblys in Office

Zur Verwendung der Funktionen einer Microsoft Office-Anwendung in einem Office-Projekt müssen Sie die primäre Interop-Assembly (PIA) für diese Anwendung verwenden. Die PIA ermöglicht es verwaltetem Code, mit dem COM-basierten Objektmodell einer Microsoft Office-Anwendung zu interagieren.  
  
Wenn Sie ein neues Office-Projekt erstellen, fügt Visual Studio Verweise auf die PIAs hinzu, die zum Erstellen des Projekts erforderlich sind. In einigen Szenarien müssen Sie Verweise auf zusätzliche PIAs hinzufügen (beispielsweise, wenn Sie eine Funktion von Microsoft Office Word in einem Projekt für Microsoft Office Excel verwenden möchten).  
  
In diesem Thema werden die folgenden Aspekte der Verwendung von Microsoft Office PIAs in Office-Projekten beschrieben:  
  
- [Separate primäre interop-Assemblys erstellen und Ausführen von Projekten](#separateassemblies)  
  
- [Verwenden von Funktionen mehrerer Microsoft Office-Anwendungen in einem einzelnen Projekt](#usingfeatures)  
  
- [Vollständige Liste primärer Interop-Assemblys für Microsoft Office-Anwendungen](#pialist)  
  
Weitere Informationen zu primären Interopassemblys finden Sie unter [primärer interop-Assemblys](http://msdn.microsoft.com/b977a8be-59a0-40a0-a806-b11ffba5c080).  

<a name="separateassemblies"></a> 

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Separate primäre interop-Assemblys erstellen und Ausführen von Projekten  

Visual Studio verwendet unterschiedliche Sätze von PIAs auf dem Entwicklungscomputer. Diese unterschiedlichen Assemblysätze befinden sich an den folgenden Speicherorten:  
  
- Einen Ordner in das Verzeichnis für Programmdateien  
  
  Diese Kopien der Assemblys werden verwendet, wenn Sie Code schreiben und Projekte erstellen. Visual Studio installiert diese Assemblys automatisch.  
  
- Im globalen Assemblycache  
  
  Diese Kopien der Assemblys werden bei einigen Entwicklungsaufgaben verwendet, z. B. wenn Sie Projekte ausführen oder debuggen. Visual Studio installiert und registriert diese Assemblys nicht; Sie müssen dies selbst tun.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Primäre interop-Assemblys in das Verzeichnis für Programmdateien  

Bei der Installation von Visual Studio werden die PIAs automatisch an einem Speicherort im Dateisystem außerhalb des globalen Assemblycaches installiert. Wenn Sie ein neues Projekt erstellen, fügt Visual Studio automatisch Verweise auf diese Kopien der PIAs zu Ihrem Projekt hinzu. Visual Studio verwendet diese PIA-Kopien anstelle der Assemblys im globalen Assemblycache, um Typverweise aufzulösen, wenn Sie das Projekt entwickeln und erstellen.  
  
Diese Kopien der PIAs helfen dabei, mehrere Entwicklungsprobleme im Zusammenhang mit Visual Studio zu vermeiden. Diese können auftreten, wenn unterschiedliche Versionen der PIAs im globalen Assemblycache registriert werden.  
  
Visual Studio installiert diese Kopien der PIAs an den folgenden Speicherorten auf dem Entwicklungscomputer:  
  
- *%ProgramFiles%\Microsoft-visual Studio 12. 0\Visual Studio Tools for Office\PIA\Office14*  
  
  (oder *% ProgramFiles% (x86) %\Microsoft Visual Studio 12. 0\Visual Studio Tools for Office\PIA\Office14* auf 64-Bit-Betriebssystemen)  
  
- *%ProgramFiles%\Microsoft-visual Studio 12. 0\Visual Studio Tools for Office\PIA\Office15*  
  
  (oder *% ProgramFiles% (x86) %\Microsoft Visual Studio 12. 0\Visual Studio Tools for Office\PIA\Office15* auf 64-Bit-Betriebssystemen)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Primäre interop-Assemblys im globalen Assemblycache  

Für die Ausführung bestimmter Entwicklungsaufgaben müssen die PIAs im globalen Assemblycache auf dem Entwicklungscomputer installiert und registriert sein. In der Regel werden die PIAs automatisch installiert, wenn Sie Office auf dem Entwicklungscomputer installieren. Weitere Informationen finden Sie unter [konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
Zur Ausführung von Office-Lösungen sind die Office-PIAs auf Endbenutzercomputern nicht erforderlich. Weitere Informationen finden Sie unter [entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md).  

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Verwenden von Funktionen mehrerer Microsoft Office-Anwendungen in einem einzelnen Projekt  

Jede Office-Projektvorlage in Visual Studio wird im Hinblick auf die Arbeit mit einer einzelnen Microsoft Office-Anwendung entworfen. Um Funktionen in mehreren Microsoft Office-Anwendungen oder in einer Anwendung bzw. Komponente zu verwenden, die kein Projekt in Visual Studio besitzt, müssen Sie einen Verweis auf die erforderlichen PIAs hinzufügen.  
  
In den meisten Fällen sollten Sie Verweise auf die PIAs, die von Visual Studio unter installiert sind Hinzufügen der `%ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\` Verzeichnis. Diese Versionen der Assemblys werden auf die **Framework** Registerkarte die **Verweis-Manager** Dialogfeld. Weitere Informationen finden Sie unter [Vorgehensweise: Target Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
Wenn Sie die PIAs im globalen Assemblycache installiert und registriert haben, werden diese Versionen im Dialogfeld **Verweis-Manager** auf der Registerkarte **COM** angezeigt. Vermeiden Sie es, Verweise auf diese Versionen hinzuzufügen, da sonst bei ihrer Verwendung Entwicklungsprobleme auftreten können. Wenn verschiedene Versionen der PIAs im globalen Assemblycache registriert sind, bindet das Projekt automatisch an die Version der Assembly, die zuletzt registriert wurde - auch dann, wenn Sie im Dialogfeld **Verweis-Manager** auf der Registerkarte **COM** eine andere Version angeben.  
  
> [!NOTE]  
>  Einige Assemblys werden einem Projekt automatisch hinzugefügt, wenn eine Assembly hinzugefügt wird, die auf sie verweist. Beispielsweise Verweise auf die *"Office.dll"* und *"Microsoft.Vbe.Interop.dll"* Assemblys werden automatisch hinzugefügt, wenn Sie einen Verweis auf die Word, Excel, Outlook, Microsoft Forms- oder Graph hinzufügen Assemblys.  

<a name="pialist"></a> 

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Primäre Interopassemblys für Microsoft Office-Anwendungen  

In der folgenden Tabelle werden die primären Interop-Assemblys aufgelistet, die für [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]verfügbar sind.  

<br/>

|Office-Anwendung oder Office-Komponente|Name der primären Interop-Assembly|  
|-------------------------------------|-----------------------------------|  
|Microsoft Access 14.0-Objektbibliothek<br /><br /> Microsoft Access 15,0-Objektbibliothek|Microsoft.Office.Interop.Access.dll|  
|Objektbibliothek der Microsoft Office 14.0 Access-Datenbank-Engine<br /><br /> Objektbibliothek der Microsoft Office 15.0 Access-Datenbank-Engine|Microsoft.Office.Interop.Access.Dao.dll|  
|Microsoft Excel 14.0-Objektbibliothek<br /><br /> Microsoft Excel 15,0-Objektbibliothek|[Microsoft.Office.Interop.Excel.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|  
|Microsoft Graph 14.0-Objektbibliothek(wird von PowerPoint, Access und Word für Diagramme verwendet)<br /><br /> Microsoft Graph 15.0-Objektbibliothek|Microsoft.Office.Interop.Graph.dll|  
|Microsoft InfoPath 2.0-Typbibliothek (nur für InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|  
|Microsoft InfoPath-XML-Interop-Assembly (nur für InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Microsoft Office 14.0-Objektbibliothek (gemeinsam genutzte Office-Funktionen)<br /><br /> Microsoft Office 15,0-Objektbibliothek (gemeinsam genutzte Office-Funktionen)|office.dll|  
|Microsoft Office Outlook-Ansichtssteuerelement (kann auf Webseiten und in Anwendungen für den Zugriff auf den Posteingang verwendet werden)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Microsoft Outlook 14.0-Objektbibliothek<br /><br /> Microsoft Outlook 15,0-Objektbibliothek|[Microsoft.Office.Interop.Outlook.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|  
|Microsoft PowerPoint 14.0-Objektbibliothek<br /><br /> Microsoft PowerPoint 15,0-Objektbibliothek|Microsoft.Office.Interop.PowerPoint.dll|  
|Microsoft Project 14.0-Objektbibliothek<br /><br /> Microsoft Project 15,0-Objektbibliothek|[Microsoft.Office.Interop.MSProject.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|  
|Microsoft Publisher 14.0-Objektbibliothek<br /><br /> Microsoft Publisher 15,0-Objektbibliothek|Microsoft.Office.Interop.Publisher.dll|  
|Microsoft SharePoint Designer 14.0-Webobjekt-Verweisbibliothek|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Microsoft SharePoint Designer 14.0-Seitenobjekt-Verweisbibliothek|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Microsoft Smart Tags 2.0-Typbibliothek **Hinweis:** Smarttags sind veraltet [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Microsoft Visio 14.0-Typbibliothek<br /><br /> Microsoft Visio 15,0-Typbibliothek|Microsoft.Office.Interop.Visio.dll|  
|Microsoft Visio 14.0-Typbibliothek für "Speichern als Web"<br /><br /> Microsoft Visio 15,0-Typbibliothek für "Speichern als Web"|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Microsoft Visio 14.0-Typbibliothek für Zeichnungssteuerelemente<br /><br /> Microsoft Visio 15,0-Typbibliothek für Zeichnungssteuerelemente|Microsoft.Office.Interop.VisOcx.dll|  
|Microsoft Word 14.0-Objektbibliothek<br /><br /> Microsoft Word 15,0-Objektbibliothek|[Microsoft.Office.Interop.Word.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.word?view=word-pia)|  
|Microsoft Visual Basic for Applications Erweiterung 5.3|Microsoft.Vbe.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Bindungsumleitungsassemblys  

Wenn Sie die Office-PIAs im globalen Assemblycache installieren und registrieren (entweder mit Office oder durch das Installieren des verteilbaren Pakets für die PIAs), werden die Bindungsumleitungsassemblys ebenfalls nur im globalen Assemblycache installiert. Diese Assemblys tragen dazu bei, die sicherstellen, dass die richtige Version der primären interop-Assemblys zur Laufzeit geladen wird. 

Wenn eine Projektmappe, die auf eine Assembly für [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] verweist, beispielsweise auf einem Computer mit der [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Version derselben primären Interop-Assembly ausgeführt wird, weist die Bindungsumleitungsassembly die [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] -Laufzeit an, die [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Version der primären Interop-Assembly zu laden. 

Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren der bindungsumleitung](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>Siehe auch  

- [Gewusst wie: Target Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
- [Übersicht über Excel-Objektmodell](../vsto/excel-object-model-overview.md)   
- [InfoPath-Lösungen](../vsto/infopath-solutions.md)   
- [Übersicht über Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)   
- [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md)   
- [Projektmappen](../vsto/project-solutions.md)   
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
- [Allgemeine Referenz &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  

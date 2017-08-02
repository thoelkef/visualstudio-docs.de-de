---
title: "PowerPoint-Projektmappen"
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
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], PowerPoint"
  - "Vorlagen [Office-Entwicklung in Visual Studio], PowerPoint"
  - "Projektmappen [Office-Entwicklung in Visual Studio], PowerPoint"
  - "Projekte [Office-Entwicklung in Visual Studio], PowerPoint"
  - "PowerPoint [Office-Entwicklung in Visual Studio]"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], PowerPoint"
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# PowerPoint-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO\-Add\-Ins für Microsoft Office PowerPoint verwenden können. Mit VSTO\-Add\-Ins können Sie PowerPoint automatisieren, PowerPoint\-Features erweitern oder die PowerPoint\-Benutzeroberfläche anpassen.  
  
 Weitere Informationen zu VSTO\-Add\-Ins finden Sie unter [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md). Wenn Sie mit dem Programmieren mit Microsoft Office noch nicht vertraut sind, lesen Sie [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 ![Link zu Video](~/docs/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Gewusst wie: Erstellen eines Add\-Ins für Microsoft PowerPoint](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## Automatisieren von PowerPoint mithilfe des PowerPoint\-Objektmodells  
 Das PowerPoint\-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von PowerPoint verwenden können. Diese Typen ermöglichen Ihnen das Schreiben von Code zum Ausführen häufiger Aufgaben:  
  
-   Programmgesteuertes Erstellen und Formatieren von Präsentationen  
  
-   Hinzufügen oder Entfernen von Folien in Präsentationen  
  
-   Hinzufügen oder Ändern von Formen in einer Folie  
  
 Wenn Sie in einem VSTO\-Add\-In auf das PowerPoint\-Objektmodell zugreifen möchten, verwenden Sie das `Application`\-Feld der `ThisAddIn`\-Klasse im Projekt. Das `Application`\-Feld gibt ein <xref:Microsoft.Office.Interop.PowerPoint.Application>\-Objekt zurück, das die aktuelle Instanz von PowerPoint darstellt. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Bei einem Aufruf des PowerPoint\-Objektmodells verwenden Sie Typen, die in der primären Interopassembly für PowerPoint bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO\-Add\-In und dem COM\-Objektmodell in PowerPoint. Alle Typen in der primären Interopassembly für PowerPoint werden im <xref:Microsoft.Office.Interop.PowerPoint>\-Namespace definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) und [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Verwenden der Dokumentation für das PowerPoint\-Objektmodell  
 Ausführliche Informationen zum PowerPoint\-Objektmodell finden Sie in der Referenz für die primäre Interopassembly \(PIA\) für PowerPoint und der VBA\-Objektmodellreferenz.  
  
### Referenz für die primäre Interopassembly  
 In der Referenzdokumentation für die PowerPoint\-PIA werden die Typen in der primären Interopassembly für PowerPoint beschrieben. Diese Dokumentation ist unter [Referenz für die primäre Interopassembly für PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588) verfügbar.  
  
 Weitere Informationen zum Entwurf der PowerPoint\-PIA \(z. B. zu Unterschieden zwischen Klassen und Schnittstellen in der PIA und zur Implementierung von Ereignissen in der PIA\) finden Sie in der [Übersicht über Klassen und Schnittstellen in den primären Interopassemblys von Office](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### VBA\-Objektmodellreferenz  
 Die VBA\-Objektmodellreferenz dokumentiert das PowerPoint\-Objektmodell, das für VBA \(Visual Basic for Applications\)\-Code verfügbar gemacht wird. Weitere Informationen finden Sie in der [PowerPoint 2010\-Objektmodellreferenz](http://go.microsoft.com/fwlink/?LinkId=199770).  
  
 Alle Objekte und Member in der VBA\-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly \(PIA\) für PowerPoint. Das Presentation\-Objekt in der VBA\-Objektmodellreferenz entspricht z. B. dem <xref:Microsoft.Office.Interop.PowerPoint.Presentation>\-Typ in der PowerPoint\-PIA. Obwohl die VBA\-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA\-Code in dieser Referenz in Visual Basic oder Visual C\# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten VSTO\-Add\-In\-Projekt für PowerPoint verwenden möchten.  
  
## Anpassen der Benutzeroberfläche von PowerPoint  
 Sie können die Benutzeroberfläche von PowerPoint folgendermaßen ändern:  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|  
|Hinzufügen von benutzerdefinierten Registerkarten zum Menüband|[Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)|  
|Hinzufügen benutzerdefinierter Gruppen zu einer integrierten Registerkarte auf dem Menüband|[Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Weitere Informationen zum Anpassen der Benutzeroberfläche von PowerPoint und anderen Microsoft Office\-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 in der Office\-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  
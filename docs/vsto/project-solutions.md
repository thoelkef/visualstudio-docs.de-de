---
title: "Projektmappen"
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
  - "Projekte [Office-Entwicklung in Visual Studio], Project"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Project"
  - "Projekt [Office-Entwicklung in Visual Studio]"
  - "Vorlagen [Office-Entwicklung in Visual Studio], Project"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Project"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Project"
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Projektmappen
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO\-Add\-Ins für Microsoft Office Project verwenden können. Mit VSTO\-Add\-Ins können Sie Project automatisieren, Project\-Features erweitern oder die Project\-Benutzeroberfläche anpassen.  
  
 Weitere Informationen zu VSTO\-Add\-Ins finden Sie unter [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md). Wenn Sie mit dem Programmieren mit Microsoft Office noch nicht vertraut sind, lesen Sie [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
## Automatisieren von Project mithilfe des Project\-Objektmodells  
 Das Project\-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Project verwenden können. Mit diesen Typen können Sie Code zum Ausführen gebräuchlicher Aufgaben schreiben, beispielsweise für das programmgesteuerte Erstellen und Ändern von Aufgaben in einem Projekt.  
  
 Wenn Sie in einem VSTO\-Add\-In auf das Project\-Objektmodell zugreifen möchten, verwenden Sie das `Application`\-Feld der `ThisAddIn`\-Klasse im Projekt. Das `Application`\-Feld gibt ein Microsoft.Office.Interop.MsProject.Application \-Objekt zurück, das die aktuelle Instanz von Project darstellt. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Bei einem Aufruf des Project\-Objektmodells verwenden Sie Typen, die in der primären Interopassembly für Project bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO\-Add\-In und dem COM\-Objektmodell in Project. Alle Typen in der primären Interopassembly für Project werden im Microsoft.Office.Interop.MSProject\-Namespace definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) und [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md).  
  
## Verwenden der Dokumentation für das Project\-Objektmodell  
 Ausführliche Informationen zum Project\-Objektmodell finden Sie in der VBA\-Objektmodellreferenz für Project. Die VBA\-Objektmodellreferenz dokumentiert das Project\-Objektmodell, das für VBA \(Visual Basic for Applications\) verfügbar gemacht wird. Weitere Informationen finden Sie in der [Project 2010\-Objektmodellreferenz](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Alle Objekte und Member in der VBA\-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly \(PIA\) für Project. Das Calendar\-Objekt in der VBA\-Objektmodellreferenz entspricht z. B. dem Microsoft.Office.Interop.MSProject.Calendar\-Typ in der Project\-PIA. Obwohl die VBA\-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA\-Code in dieser Referenz in Visual Basic oder Visual C\# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten Project\-VSTO\-Add\-In\-Projekt verwenden möchten.  
  
> [!NOTE]  
>  Derzeit ist keine Referenzdokumentation für die primäre Interopassembly für Project verfügbar.  
  
### Infrastrukturtypen in der primären Interopassembly für Project  
 Wenn Sie Code schreiben, in dem die Project\-PIA verwendet wird, werden Ihnen möglicherweise viele Typen begegnen, die nicht in der VBA\-Referenz beschrieben sind. Diese zusätzlichen Typen helfen dabei, Objekte im COM\-basierten Objektmodell von Project in verwalteten Code zu übersetzen. Sie sind nicht für die direkte Verwendung im Code vorgesehen.  
  
 Weitere Informationen finden Sie in der [Übersicht über Klassen und Schnittstellen in den primären Interopassemblys für Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## Anpassen der Benutzeroberfläche von Project  
 Sie können die Benutzeroberfläche von Project folgendermaßen anpassen:  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Hinzufügen benutzerdefinierter Registerkarten zum Menüband in Project|[Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)|  
  
 Weitere Informationen zum Anpassen der Benutzeroberfläche von Project und anderen Microsoft Office\-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Project 2010 und Project Server 2010 in der Office\-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  
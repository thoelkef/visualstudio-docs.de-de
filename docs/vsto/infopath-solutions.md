---
title: "InfoPath-Projektmappen | Microsoft Docs"
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
  - "Projektmappen [Office-Entwicklung in Visual Studio], InfoPath"
  - "Vorlagen [Office-Entwicklung in Visual Studio], InfoPath"
  - "InfoPath [Office-Entwicklung in Visual Studio]"
  - "Office-Entwicklung in Visual Studio, InfoPath-Projektmappen"
  - "Projekte [Office-Entwicklung in Visual Studio], InfoPath"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], InfoPath"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], InfoPath"
ms.assetid: 20ac6bee-b17f-4217-9f78-11304a11236a
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# InfoPath-Projektmappen
  In Visual Studio werden Projektvorlagen bereitgestellt, die Sie zum Erstellen von VSTO\-Add\-Ins für Microsoft Office InfoPath 2013 und InfoPath 2010 verwenden können. InfoPath ist in Office 2016 nicht verfügbar.  
  
> [!NOTE]  
>  Sie können trotzdem ein VSTO\-Add\-In für InfoPath erstellen, wenn Sie Office 2016 installiert haben. Installieren Sie InfoPath 2013 oder Office 2013 einfach zusätzlich zu Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
 VSTO\-Add\-Ins für InfoPath ähneln VSTO\-Add\-Ins für andere Microsoft Office\-Anwendungen. Diese Typen von Projektmappen bestehen aus einer Assembly, die von der Anwendung geladen wird. Endbenutzer können auf die Funktionen dieser Assembly zugreifen, unabhängig davon, welches Formular bzw. welche Formularvorlage geöffnet ist. Weitere Informationen zu VSTO\-Add\-Ins finden Sie unter [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 enthält nicht die InfoPath\-Formularvorlagenprojekte, die in früheren Versionen von Visual Studio bereitgestellt wurden. Sie können auch Visual Studio 2015 nicht verwenden, um ein in einer früheren Version von Visual Studio erstelltes InfoPath\-Formularvorlagenprojekt zu öffnen oder zu bearbeiten. Ein InfoPath\-Formularvorlagenprojekt kann jedoch mit Visual Studio Tools for Applications geöffnet und bearbeitet werden. Weitere Informationen finden Sie im Abschnitt zum [Arbeiten mit VSTO 2008\-Projekten in InfoPath 2010](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## Automatisieren von InfoPath mithilfe eines Add\-Ins  
 Verwenden Sie zum Zugreifen auf das InfoPath\-Objektmodell von einem Office VSTO\-Add\-In aus, das mit Office\-Entwicklungstools in Visual Studio erstellt wurde, das `Application`\-Feld der `ThisAddIn`\-Klasse im Projekt. Das `Application`\-Feld gibt ein <xref:Microsoft.Office.Interop.InfoPath.Application>\-Objekt zurück, das die aktuelle Instanz von InfoPath darstellt. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Wenn Sie von einem VSTO\-Add\-In aus Aufrufe im InfoPath\-Objektmodell ausführen, verwenden Sie Typen, die in der primären Interopassembly für InfoPath bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO\-Add\-In und dem COM\-Objektmodell in InfoPath. Alle Typen in der primären Interopassembly für InfoPath werden im <xref:Microsoft.Office.Interop.InfoPath>\-Namespace definiert. Weitere Informationen zu der primären Interopassembly für InfoPath finden Sie unter [Informationen zur primären Interopassembly für Microsoft Office InfoPath](http://msdn.microsoft.com/de-de/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Weitere Informationen zu primären Interopassemblys im Allgemeinen finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) und unter [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md).  
  
## Anpassen der Benutzeroberfläche von InfoPath mithilfe eines Add\-Ins  
 Wenn Sie ein VSTO\-Add\-In für InfoPath erstellen, haben Sie mehrere verschiedene Optionen zur Anpassung der Benutzeroberfläche. In der folgenden Tabelle werden einige dieser Optionen aufgeführt.  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|  
|Hinzufügen benutzerdefinierter Registerkarten zum Menüband in InfoPath|[Anpassen eines Menübands für InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Weitere Informationen über das Anpassen der Benutzeroberfläche von InfoPath und anderen Microsoft Office\-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## Siehe auch  
 [Informationen zur primären Interopassembly für Microsoft Office InfoPath](http://msdn.microsoft.com/de-de/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [InfoPath 2010 unter Office\-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  
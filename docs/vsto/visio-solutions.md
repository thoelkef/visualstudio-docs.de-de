---
title: "Visio-Projektmappen"
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
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Visio"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Visio"
  - "Visio [Office-Entwicklung in Visual Studio]"
  - "Vorlagen [Office-Entwicklung in Visual Studio], Visio"
  - "Projekte [Office-Entwicklung in Visual Studio], Visio"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Visio"
ms.assetid: c52948c6-6891-43ec-93ff-c54c74ec6016
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Visio-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO\-Add\-Ins für Microsoft Office Visio verwenden können. Mit VSTO\-Add\-Ins können Sie Visio automatisieren, Visio \-Features erweitern oder die Benutzeroberfläche \(User Interface, UI\) von Visio anpassen.  
  
 Weitere Informationen zu VSTO\-Add\-Ins finden Sie unter [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md). Wenn Sie mit dem Programmieren mit Microsoft Office noch nicht vertraut sind, lesen Sie [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen VSTO\-Add\-In\-Projekte für Visio 2010. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
## Automatisieren von Visio mithilfe des Visio\-Objektmodells  
 Das Visio\-Objektmodell stellt zahlreiche Klassen bereit, die Sie verwenden können, um Visio zum Erstellen von Diagrammen für Organigramme, Flussdiagramme, Projektzeitachsen, Netzwerkdiagramme, Büroräume und mehr automatisieren können. Die API ermöglicht Ihnen das Schreiben von Code zum Ausführen häufige anfallender Aufgaben:  
  
-   Erstellen und Positionieren von Shapes und Text in Diagrammen.  
  
-   Verwalten des Shape\-Verhaltens basierend auf Geschäftslogik und Benutzereingaben.  
  
-   Steuern der Darstellung von Diagrammen \(z. B. Schwenken und Zoomen\).  
  
-   Anpassen der Benutzeroberfläche der Anwendung.  
  
-   Importieren externer Daten in Visio, Verknüpfen dieser Daten mit Shapes und grafische Darstellung auf einer Seite.  
  
 Sie können schrittweise Anleitungen und Codebeispiele für die Verwendung des Visio\-Objektmodells zum Arbeiten mit Dokumenten und Shapes in [Arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md) und [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md) anzeigen.  
  
 Für den Zugriff auf das Visio\-Objektmodell aus einem VSTO\-Add\-In verwenden Sie das Feld `Application` der Klasse `ThisAddIn` in Ihrem Projekt. Das Feld `Application` gibt ein Microsoft.Office.Interop.Visio.Application\-Objekt zurück, das die aktuelle Instanz von Visio darstellt. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Bei einem Aufruf des Visio\-Objektmodells verwenden Sie Typen, die in der primären Interopassembly \(PIA\) für Visio bereitgestellt werden. Die primäre Interopassembly \(PIA\) dient als Brücke zwischen verwaltetem Code im VSTO\-Add\-In und dem COM\-Objektmodell in Visio. Alle Typen in der Visio\-PIA werden im Namespace Microsoft.Office.Interop.Visio definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) und [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md).  
  
## Übersicht über das Visio\-Objektmodell  
 Eine Übersicht über das Visio\-Objektmodell finden Sie unter [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md) – einschließlich Links zur Visio\-Objektmodellreferenz und der SDKs.  
  
## Anpassen der Benutzeroberfläche von Visio  
 Die Benutzeroberfläche von Visio weist die folgenden Anpassungsoptionen auf.  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Anpassen des Menübands.|[Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)|  
  
 Informationen zum Anpassen der Benutzeroberfläche von Visio finden Sie in der VBA\-Referenzdokumentation für die Klasse [Visio.UIObject](HV10077129).  
  
## Siehe auch  
 [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Visio 2010 unter Office\-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  
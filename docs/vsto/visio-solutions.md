---
title: Visio-Projektmappen | Microsoft Docs
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
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
ms.assetid: c52948c6-6891-43ec-93ff-c54c74ec6016
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b09e0a43f4a9dbb77a983a1f7e87f0b2886b1697
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="visio-solutions"></a>Visio-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office Visio verwenden können. Mit VSTO-Add-Ins können Sie Visio automatisieren, Visio -Features erweitern oder die Benutzeroberfläche (User Interface, UI) von Visio anpassen.  
  
 Weitere Informationen zu VSTO-Add-Ins finden Sie unter [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Wenn Sie mit Microsoft Office-Programmierung noch nicht vertraut sind, finden Sie unter [Einstieg &#40; Office-Entwicklung in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen VSTO-Add-In-Projekte für Visio 2010. Weitere Informationen finden Sie unter [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
## <a name="automating-visio-by-using-the-visio-object-model"></a>Automatisieren von Visio mithilfe des Visio-Objektmodells  
 Das Visio-Objektmodell stellt zahlreiche Klassen bereit, die Sie verwenden können, um Visio zum Erstellen von Diagrammen für Organigramme, Flussdiagramme, Projektzeitachsen, Netzwerkdiagramme, Büroräume und mehr automatisieren können. Die API ermöglicht Ihnen das Schreiben von Code zum Ausführen häufige anfallender Aufgaben:  
  
-   Erstellen und Positionieren von Shapes und Text in Diagrammen.  
  
-   Verwalten des Shape-Verhaltens basierend auf Geschäftslogik und Benutzereingaben.  
  
-   Steuern der Darstellung von Diagrammen (z. B. Schwenken und Zoomen).  
  
-   Anpassen der Benutzeroberfläche der Anwendung.  
  
-   Importieren externer Daten in Visio, Verknüpfen dieser Daten mit Shapes und grafische Darstellung auf einer Seite.  
  
 Sie können schrittweise Anleitungen und Codebeispiele für die Verwendung des Visio-Objektmodells zum Arbeiten mit Dokumenten und Shapes in [Working with Visio Documents](../vsto/working-with-visio-documents.md) und [Working with Visio Shapes](../vsto/working-with-visio-shapes.md)anzeigen.  
  
 Für den Zugriff auf das Visio-Objektmodell aus einem VSTO-Add-In verwenden Sie das Feld `Application` der Klasse `ThisAddIn` in Ihrem Projekt. Die `Application` Feld gibt ein Microsoft.Office.Interop.Visio.Application-Objekt, das die aktuelle Instanz von Visio darstellt. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Bei einem Aufruf des Visio-Objektmodells verwenden Sie Typen, die in der primären Interopassembly (PIA) für Visio bereitgestellt werden. Die primäre Interopassembly (PIA) dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in Visio. Alle Typen in der Visio-PIA werden im Microsoft.Office.Interop.Visio-Namespace definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40; VSTO- &#41; ](../vsto/office-solutions-development-overview-vsto.md) und [primären Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Übersicht über das Visio-Objektmodell  
 Eine Übersicht über das Visio-Objektmodell finden Sie unter [Visio Object Model Overview](../vsto/visio-object-model-overview.md)– einschließlich Links zur Visio-Objektmodellreferenz und der SDKs.  
  
## <a name="customizing-the-user-interface-of-visio"></a>Anpassen der Benutzeroberfläche von Visio  
 Die Benutzeroberfläche von Visio weist die folgenden Anpassungsoptionen auf.  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Anpassen des Menübands.|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|  
  
 Informationen zum Anpassen der Benutzeroberfläche von Visio finden Sie in der VBA-Referenzdokumentation für die Klasse [Visio.UIObject](https://msdn.microsoft.com/library/office/ff765763.aspx) .  
  
## <a name="see-also"></a>Siehe auch  
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Übersicht über die Entwicklung von Office-Lösungen &#40; VSTO- &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektur von VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Visio 2010 unter Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  
---
title: PowerPoint-Projektmappen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0f264cd7382ea16a7c4cfa5896241f4359b0cd67
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906045"
---
# <a name="powerpoint-solutions"></a>PowerPoint-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office PowerPoint verwenden können. Mit VSTO-Add-Ins können Sie PowerPoint automatisieren, PowerPoint-Features erweitern oder die PowerPoint-Benutzeroberfläche anpassen.  
  
 Weitere Informationen zu VSTO-Add-ins finden Sie unter [erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architecture of VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md). Wenn Sie die mit Microsoft Office-Programmierung vertraut sind, finden Sie unter [Einstieg &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  Möchten Sie bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins verfügen, einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
 ![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Erstellen Sie ein Add-in für Microsoft PowerPoint? ](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatisieren von PowerPoint mithilfe von PowerPoint-Objektmodell  
 Das PowerPoint-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von PowerPoint verwenden können. Diese Typen ermöglichen Ihnen das Schreiben von Code zum Ausführen häufiger Aufgaben:  
  
- Programmgesteuertes Erstellen und Formatieren von Präsentationen  
  
- Hinzufügen oder Entfernen von Folien in Präsentationen  
  
- Hinzufügen oder Ändern von Formen in einer Folie  
  
  Um das PowerPoint-Objektmodell aus einem VSTO-Add-in zuzugreifen, verwenden die `Application` Feld der `ThisAddIn` Klasse im Projekt. Das `Application` -Feld gibt ein <xref:Microsoft.Office.Interop.PowerPoint.Application> -Objekt zurück, das die aktuelle Instanz von PowerPoint darstellt. Weitere Informationen finden Sie unter [Programm VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
  Bei einem Aufruf des PowerPoint-Objektmodells verwenden Sie Typen, die in der primären Interopassembly für PowerPoint bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in PowerPoint. Alle Typen in der primären Interopassembly für PowerPoint werden im <xref:Microsoft.Office.Interop.PowerPoint> -Namespace definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) und [primären Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Verwenden der Dokumentation für das PowerPoint-Objektmodell  
 Ausführliche Informationen zum PowerPoint-Objektmodell finden Sie in der Referenz für die primäre Interopassembly (PIA) für PowerPoint und der VBA-Objektmodellreferenz.  
  
### <a name="primary-interop-assembly-reference"></a>Primäre interop-Assembly-Verweis  
 In der Referenzdokumentation für die PowerPoint-PIA werden die Typen in der primären Interopassembly für PowerPoint beschrieben. Diese Dokumentation ist aus folgendem Ort verfügbar: [Referenz für die primäre interop-Assembly von PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Weitere Informationen zum Entwurf der PowerPoint-PIA, z. B. zu Unterschieden zwischen Klassen und Schnittstellen in der PIA und zur Implementierung von Ereignissen in der PIA, finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interopassemblys für Office ](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>VBA-Objektmodellreferenz  
 Die VBA-Objektmodellreferenz dokumentiert das PowerPoint-Objektmodell, das für VBA (Visual Basic for Applications)-Code verfügbar gemacht wird. Weitere Informationen finden Sie unter [PowerPoint 2010-Objektmodellreferenz](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly (PIA) für PowerPoint. Z. B. das Presentation-Objekt in der VBA-Objektmodellreferenz entspricht der <xref:Microsoft.Office.Interop.PowerPoint.Presentation> -Typ in der PowerPoint-PIA. Obwohl die VBA-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder Visual C# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten VSTO-Add-In-Projekt für PowerPoint verwenden möchten.  
  
## <a name="customize-the-user-interface-of-powerpoint"></a>Anpassen der Benutzeroberfläche von PowerPoint  
 Sie können die Benutzeroberfläche von PowerPoint folgendermaßen ändern:  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|  
|Hinzufügen von benutzerdefinierten Registerkarten zum Menüband|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|  
|Hinzufügen benutzerdefinierter Gruppen zu einer integrierten Registerkarte auf dem Menüband|[Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Weitere Informationen zum Anpassen der Benutzeroberfläche von PowerPoint und anderen Microsoft Office-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)   
 [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 unter Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199015)  

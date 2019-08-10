---
title: PowerPoint-Lösungen
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d2c85a4af986c62d3e3f3c3a3f4333baa2975ee
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926430"
---
# <a name="powerpoint-solutions"></a>PowerPoint-Lösungen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office PowerPoint verwenden können. Mit VSTO-Add-Ins können Sie PowerPoint automatisieren, PowerPoint-Features erweitern oder die PowerPoint-Benutzeroberfläche anpassen.

 Weitere Informationen zu VSTO-Add-Ins finden Sie unter "Einstieg in die [Programmierung von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO](../vsto/architecture-of-vsto-add-ins.md)-Add-Ins". Wenn Sie noch nicht mit der Programmierung mit Microsoft Office vertraut sind, finden Sie weitere Informationen unter [ &#40;Office-Entwicklung in Visual&#41;Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

> [!NOTE]
> Möchten Sie Lösungen entwickeln, die die Office-Funktionen auf [mehrere Plattformen](https://dev.office.com/add-in-availability)ausweiten? Sehen Sie sich das neue [Office-Add-ins-Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins)an. Office-Add-ins haben im Vergleich zu VSTO-Add-Ins und-Lösungen einen geringen Speicherbedarf, und Sie können Sie mithilfe von fast allen webprogrammierungs Technologien wie HTML5, JavaScript, CSS3 und XML erstellen.

 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") Eine entsprechende videodemo finden [Sie unter Gewusst wie: Erstellen Sie ein Add-in für Microsoft PowerPoint? ](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatisieren von PowerPoint mithilfe des PowerPoint-Objektmodells
 Das PowerPoint-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von PowerPoint verwenden können. Diese Typen ermöglichen Ihnen das Schreiben von Code zum Ausführen häufiger Aufgaben:

- Programmgesteuertes Erstellen und Formatieren von Präsentationen

- Hinzufügen oder Entfernen von Folien in Präsentationen

- Hinzufügen oder Ändern von Formen in einer Folie

  Wenn Sie über ein VSTO-Add-in auf das PowerPoint-Objekt `Application` Modell zugreifen möchten `ThisAddIn` , verwenden Sie das-Feld der-Klasse im Projekt. Das `Application` -Feld gibt ein- [Anwendungs](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) Objekt zurück, das die aktuelle Instanz von PowerPoint darstellt. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

  Bei einem Aufruf des PowerPoint-Objektmodells verwenden Sie Typen, die in der primären Interopassembly für PowerPoint bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in PowerPoint. Alle Typen in der primären Interopassembly für PowerPoint werden im Namespace [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht &#40;über die Entwicklung&#41; von Office](../vsto/office-solutions-development-overview-vsto.md) -Projektmappen VSTO und [Office Primary](../vsto/office-primary-interop-assemblies.md)Interopassemblys

## <a name="WordOMDocumentation"></a>Verwenden der Dokumentation zum PowerPoint-Objektmodell
 Ausführliche Informationen zum PowerPoint-Objektmodell finden Sie in der Referenz für die primäre Interopassembly (PIA) für PowerPoint und der VBA-Objektmodellreferenz.

### <a name="primary-interop-assembly-reference"></a>Referenz zur primären Interopassembly
 In der Referenzdokumentation für die PowerPoint-PIA werden die Typen in der primären Interopassembly für PowerPoint beschrieben. Diese Dokumentation ist unter folgendem Speicherort verfügbar: [PowerPoint 2010 primärer](http://go.microsoft.com/fwlink/?LinkId=189588)interopassemblyverweis.

 Weitere Informationen zum Entwurf der PowerPoint-Pia, z. b. zu den Unterschieden zwischen Klassen und Schnittstellen in der Pia und zur Implementierung von Ereignissen in der Pia, finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interop](http://go.microsoft.com/fwlink/?LinkId=199885)-Assemblys von Office.

### <a name="vba-object-model-reference"></a>VBA-Objektmodell Referenz
 Die VBA-Objektmodellreferenz dokumentiert das PowerPoint-Objektmodell, das für VBA (Visual Basic for Applications)-Code verfügbar gemacht wird. Weitere Informationen finden Sie unter [PowerPoint 2010-Objektmodell Referenz](http://go.microsoft.com/fwlink/?LinkId=199770).

 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly (PIA) für PowerPoint. Das Präsentationsobjekt in der VBA-Objektmodell Referenz entspricht z. b. dem [Präsentationstyp](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) in der PowerPoint-Pia. Obwohl die VBA-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder Visual C# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten VSTO-Add-In-Projekt für PowerPoint verwenden möchten.

## <a name="customize-the-user-interface-of-powerpoint"></a>Anpassen der Benutzeroberfläche von PowerPoint
 Sie können die Benutzeroberfläche von PowerPoint folgendermaßen ändern:

|Aufgabe|Weitere Informationen|
|----------|--------------------------|
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|
|Hinzufügen von benutzerdefinierten Registerkarten zum Menüband|[Übersicht über Menüband](../vsto/ribbon-overview.md)|
|Hinzufügen benutzerdefinierter Gruppen zu einer integrierten Registerkarte auf dem Menüband|[Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|

 Weitere Informationen zum Anpassen der Benutzeroberfläche von PowerPoint und anderen Microsoft Office Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erstellen Ihres ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
- [Übersicht über &#40;die Entwicklung von Office-Lösungen VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)
- [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [PowerPoint 2010 bei der Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199015)

---
title: Projektmappen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5fe9f47fca2b83e0095c67e59c2db54a4a04159
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447060"
---
# <a name="project-solutions"></a>Projektmappen
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office Project verwenden können. Mit VSTO-Add-Ins können Sie Project automatisieren, Project-Features erweitern oder die Project-Benutzeroberfläche anpassen.

 Weitere Informationen zu VSTO-Add-ins finden Sie unter [erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architecture of VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md). Wenn Sie die mit Microsoft Office-Programmierung vertraut sind, finden Sie unter [Einstieg &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

> [!NOTE]
> Möchten Sie bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins verfügen, einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.

## <a name="automate-project-by-using-the-project-object-model"></a>Automatisieren von Project mithilfe von Project-Objektmodell
 Das Project-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Project verwenden können. Mit diesen Typen können Sie Code zum Ausführen gebräuchlicher Aufgaben schreiben, beispielsweise für das programmgesteuerte Erstellen und Ändern von Aufgaben in einem Projekt.

 Um die Project-Objektmodell aus einem VSTO-Add-in zuzugreifen, verwenden die `Application` Feld der `ThisAddIn` Klasse im Projekt. Die `Application` Feld gibt einen `Microsoft.Office.Interop.MsProject.Application` Objekt, das die aktuelle Instanz von Project darstellt. Weitere Informationen finden Sie unter [Programm VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

 Bei einem Aufruf des Project-Objektmodells verwenden Sie Typen, die in der primären Interopassembly für Project bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in Project. Alle Typen in der primären Interopassembly für Project werden im `Microsoft.Office.Interop.MSProject`-Namespace definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) und [primären Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Verwenden der Dokumentation für das Project-Objektmodell
 Ausführliche Informationen zum Project-Objektmodell finden Sie in der VBA-Objektmodellreferenz für Project. Die VBA-Objektmodellreferenz dokumentiert das Project-Objektmodell, das für VBA (Visual Basic for Applications) verfügbar gemacht wird. Weitere Informationen finden Sie unter [Project 2010-Objektmodellreferenz](http://go.microsoft.com/fwlink/?LinkId=199771).

 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly (PIA) für Project. Z. B. das Kalender-Objekt in der VBA-Objektmodellreferenz entspricht der `Microsoft.Office.Interop.MSProject.Calendar` Typ in der Project-PIA. Obwohl die VBA-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder Visual c# übersetzen, sollten Sie diese in einem Project-VSTO-Add-in-Projekt verwenden, die Sie erstellen mithilfe von Visual Studio.

> [!NOTE]
> Derzeit ist keine Referenzdokumentation für die primäre Interopassembly für Project verfügbar.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Infrastrukturtypen in der primären Interopassembly für project
 Wenn Sie Code schreiben, in dem die Project-PIA verwendet wird, werden Ihnen möglicherweise viele Typen begegnen, die nicht in der VBA-Referenz beschrieben sind. Diese zusätzlichen Typen helfen dabei, Objekte im COM-basierten Objektmodell von Project in verwalteten Code zu übersetzen. Sie sind nicht für die direkte Verwendung im Code vorgesehen.

 Weitere Informationen finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interopassemblys für Office](http://go.microsoft.com/fwlink/?LinkId=189592).

## <a name="customize-the-user-interface-of-project"></a>Anpassen der Benutzeroberfläche des Projekts
 Sie können die Benutzeroberfläche von Project folgendermaßen anpassen:

|Aufgabe|Weitere Informationen|
|----------|--------------------------|
|Hinzufügen benutzerdefinierter Registerkarten zum Menüband in Project|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|

 Weitere Informationen zum Anpassen der Benutzeroberfläche von Project und anderen Microsoft Office-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
- [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)
- [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)
- [Project 2010 und Project Server 2010 unter Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199016)

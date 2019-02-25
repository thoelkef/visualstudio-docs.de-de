---
title: Verfügbare Funktionen nach Office-Anwendung und Projekt geben.
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2cff118e31a10780a4573608a6516ddea9e4f73a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626751"
---
# <a name="features-available-by-office-application-and-project-type"></a>Verfügbare Funktionen nach Office-Anwendung und Projekt geben.
  Visual Studio verfügt über mehrere Arten von Projektvorlagen, die unterschiedliche Geschäftsszenarien für Microsoft Office-Anwendungen unterstützen, z. B.:

- Anpassungen auf Dokumentebene

- VSTO-Add-Ins

  Nicht alle Anwendungen können jeden Projekttyp verwenden. Beispielsweise sind Projekte auf Dokumentebene nur für Microsoft Office Word und Microsoft Office Excel verfügbar. Ebenso sind einige Features nur für bestimmte Projekt- oder Anwendungstypen verfügbar. Der Aktionsbereich ist beispielsweise nur in Projekten auf Dokumentebene verfügbar, und Menübanderweiterungen stehen nur für einige Anwendungen zur Verfügung. Weitere Informationen zu den unterschiedlichen Projekttypen, finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
>  Office-Projektvorlagen sind nur in einigen Editionen von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügbar. Weitere Informationen finden Sie unter [konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Für andere Microsoft Office-Anwendungen verfügbare Projekttypen
 In der folgenden Tabelle sind die Anwendungen aufgeführt, die Sie für die einzelnen Projekttypen verwenden können.

|Projekttypen|Microsoft Office-Anwendung|
|-------------------|----------------------------------|
|Anpassungen auf Dokumentebene|Excel<br /><br /> Word|
|VSTO-Add-Ins|Excel<br /><br /> InfoPath (nur InfoPath 2013 und InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>In Projekttypen verfügbare Funktionen
 In der folgenden Tabelle ist aufgeführt, für welche Projekttypen die jeweilige Funktion bereitgestellt wird.

|Feature|Projekttypen, die das Feature bereitstellen|Weiterführende Themen|
|-------------|--------------------------------------------|---------------------|
|Aktionsbereich|Projekte auf Dokumentebene|[Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)|
|ClickOnce-Bereitstellung:|VS-Projekte und Projekte auf Dokumentebene|[Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)|
|Benutzerdefinierte Aufgabenbereiche|VSTO-Add-In-Projekte für die folgenden Anwendungen:<br /><br /> -   Excel<br />-InfoPath (InfoPath 2013 und InfoPath 2010 nur)<br />-   Outlook<br />-PowerPoint<br />-Word|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|
|Benutzerdefinierte XML-Teile|Projekte auf Dokumentebene<br /><br /> Projekte auf Anwendungsebene für die folgenden Anwendungen:<br /><br /> -   Excel<br />-PowerPoint<br />-Word|[Übersicht über benutzerdefinierte XML-Teile](../vsto/custom-xml-parts-overview.md)|
|Datencache|Projekte auf Dokumentebene|[Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md)|
|Machen Sie ein Objekt in einem VSTO-Add-in für andere Microsoft Office-Projektmappen verfügbar.|VSTO-Add-In-Projekte|[Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Folgende Hoststeuerelemente:<br /><br /> -Diagramm<br />-ListObject<br />-NamedRange<br />– Content-Steuerelementen<br />-Lesezeichen|Projekte auf Dokumentebene<br /><br /> VSTO-Add-In-Projekte für Word und Excel|[Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)|
|Folgende Hoststeuerelemente:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Projekte auf Dokumentebene|[Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)|
|Bereitstellung von mehreren Projekten|Projekte auf Dokumentebene<br /><br /> VSTO-Add-In-Projekte|[Exemplarische Vorgehensweise: Bereitstellen von mehreren Office-Projektmappen in einem einzelnen ClickOnce-installer](https://msdn.microsoft.com/051223c0-4082-4799-b78b-a4763a9def55)|
|Outlook-Formularbereiche|VSTO-Add-In-Projekte für Outlook|[Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)|
|Aktionen nach der Bereitstellung|Projekte auf Dokumentebene<br /><br /> VSTO-Add-In-Projekte|[Exemplarische Vorgehensweise: Kopieren Sie ein Dokument auf dem Computer des Endbenutzers nach einer ClickOnce-installation](https://msdn.microsoft.com/100090f7-bc63-4152-b3e1-19b48bc27466)|
|Menübandanpassungen|Projekte auf Dokumentebene<br /><br /> VSTO-Add-In-Projekte für die folgenden Anwendungen:<br /><br /> -   Excel<br />-InfoPath (InfoPath 2013 und InfoPath 2010 nur)<br />-   Outlook<br />-PowerPoint<br />-Projekt<br />-   Visio<br />-Word|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|
|Visueller Dokumentdesigner|Projekte auf Dokumentebene|[Office-Projekten in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Siehe auch
- [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md)
- [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)

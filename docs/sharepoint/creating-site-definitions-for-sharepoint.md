---
title: Erstellen von Website Definitionen für SharePoint | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a75b7143412d360a7663e7cf94a1244d66d15a2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984522"
---
# <a name="create-site-definitions-for-sharepoint"></a>Erstellen von Website Definitionen für SharePoint
  Mit dem SharePoint-Website Definitions Projekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] können Sie eine *Website Definition*erstellen, die als Grundlage für eine neue SharePoint-Website dient. Diese Definitionen bestimmen nicht nur die Darstellung und das Verhalten der SharePoint-Website, sondern auch die Standard Inhalte und-Funktionen. In der Definition können Sie vorkonfigurierte Listen, Inhaltstypen, Ereignis Empfänger, Bilder und andere Elemente platzieren. SharePoint enthält beispielsweise einige Site Definitionen, z. b. Blog. Wenn Sie eine Website basierend auf der Definition der Blog Site erstellen, enthält die Website die Listen, Webparts und andere Elemente, die für eine Blogsite erforderlich sind.

 Weitere Informationen zu Site Definitionen finden Sie unter [Website Vorlagen und Definitionen](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Site Definitions Projekte
 Site Definitions Projekte in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nur die grundlegenden Dateien bereitstellen, die von einer SharePoint-Website benötigt werden. Sie stellen keine Standardfunktionen bereit. Sie müssen Dateien und Inhalte hinzufügen, um die gewünschte Funktionalität bereitzustellen. Sie können die Website manuell erstellen, indem Sie die benötigten Dateien erstellen und hinzufügen.

## <a name="feature-stapling"></a>Featureheftung
 Ein Vorteil beim Erstellen von Website Definitionen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] besteht darin, dass Sie die *Featureheftung*automatisch verwenden. Durch die Featureheftung wird eine Funktion an eine Website Definition angefügt, anstatt ihre Funktionalität in die Website Definition einzubetten. Auf diese Weise können Sie die Funktion zu jeder Website hinzufügen, die mithilfe der Website Definition erstellt wurde, ohne die ursprüngliche Site Definition zu ändern. Weitere Informationen finden Sie unter [Featureheftung](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Site Definition-Projektkomponenten
 Beim Erstellen einer Site Definitions Lösung werden dem **Sitedefinition** -Knoten die folgenden Standard Dateien hinzugefügt.

|Dateiname|Beschreibung|
|---------------|-----------------|
|*default. aspx*|Die Standard-aspx-Startseite für die neue SharePoint-Website.|
|*"Onet. xml"*|Gibt die Konfiguration des neuen Standorts, die Komponenten der Site Definitions Vorlage und das Standardverhalten an. Diese Einstellungen können Attribute wie z. b. aktivierte Inhaltstypen, die Standard Listen Sichten, Dokumentvorlagen Dateien und Webparts enthalten, die in der Website enthalten sind. Der `Modules` Abschnitt listet standardmäßig die Dateien auf, die der SharePoint-Website hinzugefügt werden sollen, und wie Sie konfiguriert werden.|
|*webtemp_\<SiteDefinitionName >. XML*|Gibt die Site Definitions Konfigurationen an, die im Abschnitt **Vorlagen Auswahl** der Seite **neue SharePoint-Website** angezeigt werden.|

 Standardmäßig werden alle Site Definitionen im Ordner *\<Laufwerk: > \Programme\Gemeinsame Dateien\Microsoft Shared\Web Server extensions\14\template\sitetemplates* gespeichert. Jede Site Definition verfügt über einen eigenen Unterordner.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts für eine Websitedefinition](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Führt Sie Schritt für Schritt durch die Erstellung eines einfachen Projekts für eine Website Definition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Vorgehensweise: Erstellen einer benutzerdefinierten Site Definition und Konfiguration](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Beschreibt, wie eine benutzerdefinierte Site Definition in SharePoint erstellt wird, indem eine vorhandene Website Definition kopiert und die Kopie anschließend geändert wird.|
|[*Webtemp. XML*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Beschreibt die ursprüngliche Datei, in der die Site Definitionen angegeben sind, die im Abschnitt **Vorlagen Auswahl** der Seite **neue SharePoint-Website** verfügbar sind.|
|[Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)|Beschreibt, wie die SharePoint-Lösungen für die globale Verwendung vorbereitet werden.|
|[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Beschreibt, wie Sie Teile einer SharePoint-Seite erstellen können, die von Benutzern geändert werden können.|
|[Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungs Seiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Beschreibt, wie Sie wiederverwendbare Steuerelemente erstellen können, die auf Anwendungs Seiten und Webparts ausgeführt werden.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Beschreibt die Verwendung des Designers, der angezeigt wird, wenn Sie eine Webseite in Ihrem Projekt öffnen.|
|[Übersicht über ASP.net Web Pages](/previous-versions/aspnet/428509ah(v=vs.100))|Bietet allgemeine Informationen über die Struktur [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Webseiten, die Art und Weise, wie Seiten von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]verarbeitet werden, und wie [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten Markup anzeigen, das den XHTML-Standards entspricht.|
|[Syntax der ASP.NET-Webseite](/previous-versions/aspnet/k33801s3(v=vs.100))|Beschreibt die Markup Elemente, die eine ASP.NET Seite bilden.|
|[Programmier ASP.net Web Pages](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Stellt Informationen zum Erstellen von Ereignis Handlern in [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten und zum Arbeiten mit Client Skripts bereit.|
|[Programmieren in Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Beschreibt, wie das verwaltete Objektmodell verwendet wird, das in [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]bereitgestellt wird.|

## <a name="see-also"></a>Siehe auch
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)

---
title: Erstellen von Websitedefinitionen für SharePoint | Microsoft-Dokumentation
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
ms.openlocfilehash: 2abf61bbc960e342a395e9c0ff3395ecde852137
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604867"
---
# <a name="create-site-definitions-for-sharepoint"></a>Erstellen von Websitedefinitionen für SharePoint
  Das Projekt für SharePoint-Sitedefinition im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ermöglicht das Erstellen einer *Websitedefinition*, die dient als Grundlage für eine neue SharePoint-Website. Diese Definitionen bestimmen nicht nur das Aussehen und Verhalten der SharePoint-Website, aber auch den Standardinhalt und Funktionalität. In der Definition können Sie die vorkonfigurierten Listen, Inhaltstypen, Ereignisempfänger, Bilder und andere Elemente einfügen. SharePoint bietet einige Websitedefinitionen, z. B. BLOG, z. B. aus. Wenn Sie einen Standort, basierend auf der Definition der BLOG-Website erstellen, enthält den Standort, die Listen, Webparts und andere Elemente, die eine Blogwebsite erfordert.

 Weitere Informationen zu Websitedefinitionen, finden Sie unter [Websitevorlagen und Definitionen](http://go.microsoft.com/fwlink/?LinkId=179134).

## <a name="site-definition-projects"></a>Definition von Websiteprojekten
 Definition Websiteprojekte in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nur die grundlegenden Dateien, die eine SharePoint-Website muss, sondern sie bieten keine Standardfunktionen. Dateien und Inhalte zum Bereitstellen der Funktionen, die Sie möchten, müssen Sie hinzufügen. Sie können den Standort manuell erstellen, indem erstellen und Hinzufügen der Dateien, die Sie benötigen.

## <a name="feature-stapling"></a>Heften Funktion
 Ein Vorteil beim Erstellen von Websitedefinitionen im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] besteht darin, dass sie automatisch verwenden *Feature Heften*. Feature Heftung Fügt eine Funktion an eine Sitedefinition, statt die Funktionalität in die Sitedefinition an. Auf diese Weise können Sie die Funktion auf einem beliebigen Standort mithilfe der Websitedefinition ohne Änderung der ursprünglichen Websitedefinition erstellt hinzufügen. Weitere Informationen finden Sie unter [Feature Heften](http://go.microsoft.com/fwlink/?LinkID=119283).

## <a name="site-definition-project-components"></a>Standortkomponenten-Definition-Projekt
 Bei der Erstellung einer Sitedefinition werden die folgenden Standarddateien hinzugefügt, um die **SiteDefinition** Knoten.

|Dateiname|Beschreibung|
|---------------|-----------------|
|*default.aspx*|Die standardmäßige ASPX-Homepage für die neue SharePoint-Website.|
|*onet.xml*|Gibt an, die Konfiguration des neuen Standorts, die Komponenten der Websitevorlage für die Definition und Standardverhalten. Diese Einstellungen können zählen etwa Attribute wie die Inhaltstypen, die aktiviert sind, den standardmäßigen Listenansichten Dokument Vorlagendateien und Webparts, die mit dem Standort enthalten. In der Standardeinstellung die `Modules` Abschnitt listet die Dateien hinzugefügt werden, die SharePoint-Website und wie sie konfiguriert sind.|
|*webtemp_\<SiteDefinitionName>.xml*|Gibt an, die Websitedefinitionskonfigurationen, die in angezeigt wird. die **Vorlagenauswahl** Teil der **neue SharePoint-Website** Seite.|

 Standardmäßig befinden sich alle Website-Definitionen der  *\<Laufwerk: > \Programme\Gemeinsame Dateien\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* Ordner. Jede Sitedefinition verfügt über einen eigenen Unterordner.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts Definition](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Führt Sie Schritt für Schritt durch die Erstellung von grundlegenden sitedefinitionsprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Vorgehensweise: Erstellen Sie eine benutzerdefinierte Sitedefinition und Konfiguration](http://go.microsoft.com/fwlink/?LinkId=183309)|Beschreibt, wie eine benutzerdefinierte Sitedefinition in SharePoint erstellen, durch Kopieren einer vorhandenen Definition für den Standort aus, und klicken Sie dann die Kopie ändern.|
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|Beschreibt die ursprüngliche Datei, der angibt, die Websitedefinitionen zur Verfügung, in der **Vorlagenauswahl** im Abschnitt der **neue SharePoint-Website** Seite.|
|[Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)|Beschreibt, wie die SharePoint-Lösungen für die globale Verwendung vorzubereiten.|
|[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Beschreibt, wie Sie Teile einer SharePoint-Seite erstellen, die Benutzer ändern können.|
|[Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Beschreibt, wie Sie wiederverwendbare Steuerelemente erstellen können, die in Anwendungsseiten und Webparts ausgeführt.|
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Beschreibt, wie den Designer verwendet, der angezeigt wird, wenn Sie in Ihrem Projekt eine Webseite öffnen.|
|[Übersicht über die ASP.NET Web Pages](http://go.microsoft.com/fwlink/?LinkId=178726)|Bietet allgemeine Informationen zur Struktur von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Webseiten, wie Seiten verarbeitet werden, indem [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], und wie [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten Markup anzeigen, das mit XHTML-Standards kompatibel ist.|
|[Syntax von ASP.NET-Seiten Web](http://go.microsoft.com/fwlink/?LinkId=178727)|Beschreibt die Markupelemente, die eine ASP.NET-Seite bilden.|
|[Programmierung von ASP.NET-Webseiten](http://go.microsoft.com/fwlink/?LinkId=178728)|Enthält Informationen über das Erstellen von Ereignishandlern in [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten und Arbeiten mit Clientskript.|
|[Programmieren in Windows SharePointServices](http://go.microsoft.com/fwlink/?LinkId=178729)|Beschreibt, wie Sie das verwaltete Objektmodell verwenden, die in bereitgestellt wird [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|

## <a name="see-also"></a>Siehe auch
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)

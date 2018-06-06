---
title: Erstellen von Websitedefinitionen für SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1fae92a9ca958f3d6702ec0f2d1678b33d471bab
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765491"
---
# <a name="create-site-definitions-for-sharepoint"></a>Erstellen von Websitedefinitionen für SharePoint
  Die Definition des SharePoint-Projekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ermöglicht die Erstellung einer *Websitedefinition*, dem dient als Grundlage für eine neue SharePoint-Website. Diese Definitionen bestimmen nicht nur das Aussehen und Verhalten von der SharePoint-Website jedoch auch den Standardinhalt und Funktionalität. In der Definition können Sie vorkonfigurierte Listen, Inhaltstypen, Ereignisempfänger, Bilder und andere Elemente einfügen. SharePoint schließt einige Websitedefinitionen wie BLOG verwenden, z. B. aus. Wenn Sie einen Standort basierend auf der Definition der BLOG-Website erstellen, enthält den Standort, die Listen, Webparts und andere Elemente, die eine Blogwebsite erfordert.  
  
 Weitere Informationen zu Websitedefinitionen, finden Sie unter [Websitevorlagen und Definitionen](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Definition Websiteprojekten
 Definition Websiteprojekte in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nur die grundlegenden Dateien, die eine SharePoint-Website muss, sondern sie keinen keine Standardfunktionen. Sie müssen die Dateien und der Inhalt der Funktionalität bereit, die gewünschten hinzufügen. Sie können den Standort erstellen und Hinzufügen der Dateien, die Sie benötigen, manuell erstellen.  
  
## <a name="feature-stapling"></a>Heften Funktion
 Ein Vorteil beim Erstellen von Websitedefinitionen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ist, dass automatisch *Feature Heften*. Feature Heften Fügt eine Funktion an einer Websitedefinition anstatt seine Funktionalität in die Sitedefinition einzubetten. Auf diese Weise können Sie die Funktion mit einem beliebigen Standort mithilfe der Sitedefinition ohne Ändern der Standortdefinition des ursprünglichen erstellt hinzufügen. Weitere Informationen finden Sie unter [Feature Heften](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Standortkomponenten Definition-Projekt
 Wenn Sie eine sitedefinitionslösung erstellen, die folgenden Standarddateien hinzugefügt werden seine **SiteDefinition** Knoten.  
  
|Dateiname|Beschreibung|  
|---------------|-----------------|  
|*"default.aspx"*|Die standardmäßige ASPX-Homepage für die neue SharePoint-Website.|  
|*onet.Xml*|Gibt an, die Konfiguration des neuen Standorts, die Komponenten der Definition der Websitevorlage und Standardverhalten. Diese Einstellungen umfassen Attribute wie z. B. die Inhaltstypen, die aktiviert und den standardmäßigen Listenansichten Dokument Vorlagendateien zu und Webparts mit dem Standort enthalten. Wird standardmäßig die `Modules` Abschnitt listet die Dateien hinzugefügt werden, um die SharePoint-Website und wie diese konfiguriert werden.|  
|*Webtemp_ {SiteDefinitionName} .xml*|Gibt an, die Websitedefinitionskonfigurationen, die in angezeigt wird der **Vorlagenauswahl** Teil der **neue SharePoint-Website** Seite.|  
  
 Standardmäßig werden alle Websitedefinitionen gespeichert, der *{Laufwerk:} \Programme\Gemeinsame Dateien\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* Ordner. Jedes Site-Definition verfügt über einen eigenen Unterordner.  
  
## <a name="related-topics"></a>Verwandte Themen
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts für eine Websitedefinition](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Führt Sie schrittweise durch die Erstellung einer einfachen Projekts Websitedefinition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Vorgehensweise: Erstellen einer benutzerdefinierten Sitedefinition und Konfiguration](http://go.microsoft.com/fwlink/?LinkId=183309)|Beschreibt, wie eine Websitedefinition für die benutzerdefinierte in SharePoint erstellen, durch Kopieren einer vorhandenen Websitedefinition und diese dann ändern.|  
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|Beschreibt die ursprüngliche Datei, die in verfügbaren Websitedefinitionen gibt die **Vorlagenauswahl** Teil der **neue SharePoint-Website** Seite.|  
|[Lokalisieren von SharePoint-Projektmappen](../sharepoint/localizing-sharepoint-solutions.md)|Beschreibt, wie die SharePoint-Lösungen für die globale Verwendung vorbereiten.|  
|[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Beschreibt, wie Sie Teile einer SharePoint-Seite erstellen können, die Benutzer ändern können.|  
|[Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Beschreibt, wie Sie wiederverwendbare Steuerelemente erstellen können, die in Anwendungsseiten und Webparts ausgeführt.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Beschreibt, wie den Designer, der angezeigt wird, wenn Sie in Ihrem Projekt eine Webseite geöffnet.|  
|[ASP.NET Web Pages (Übersicht)](http://go.microsoft.com/fwlink/?LinkId=178726)|Enthält allgemeine Informationen zur Struktur von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Webseiten, wie Seiten verarbeitet werden, indem [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], und wie [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten anzeigen Markup, das mit XHTML-Standards entspricht.|  
|[ASP.NET Web-Seite-Syntax](http://go.microsoft.com/fwlink/?LinkId=178727)|Beschreibt die Markupelemente, aus denen eine ASP.NET-Seite besteht.|  
|[Programmieren von ASP.NET Web Pages](http://go.microsoft.com/fwlink/?LinkId=178728)|Enthält Informationen über das Erstellen von Ereignishandlern in [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten und zum Arbeiten mit Clientskripts.|  
|[In Windows SharePointServices-Programmierung](http://go.microsoft.com/fwlink/?LinkId=178729)|Beschreibt, wie das verwaltete Objektmodell verwenden, die in bereitgestellten [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Siehe auch
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
 

---
title: Erstellen von Anwendungsseiten für SharePoint | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8f02fbff9ed727359adbc5db1b25ee14dbccb3a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644444"
---
# <a name="create-application-pages-for-sharepoint"></a>Erstellen von Anwendungsseiten für SharePoint
  Ein *Anwendungsseite* ist eine ASP.NET Web-Seite, die für die Verwendung in einer SharePoint-Website entwickelt wurde. Anwendungsseiten sind ein spezieller Typ von der ASP.NET-Seite. Der Hauptunterschied zwischen einer Anwendungsseite und einer standardmäßigen ASP.NET-Seite ist, dass eine Anwendungsseite Inhalt enthält, das mit einer SharePoint-Masterseite zusammengeführt wird. Eine Masterseite ermöglicht Anwendungsseiten zur Darstellung und Verhalten wie andere Seiten auf einer Website freigeben.

 Visual Studio ermöglicht Ihnen, mithilfe eines Designers Anwendungsseiten zu entwerfen. Der Designer zeigt einen Inhaltsbereich jedes für Platzhalter für Inhalte, die auf einer Masterseite definiert ist. Sie können die Seite "Anwendung" Entwerfen, durch Ziehen von Steuerelementen auf diese Inhalte Bereiche.

## <a name="application-pages"></a>Anwendungsseiten
 Anwendungsseiten werden für alle Sites auf dem Server freigegeben, während eine Websiteseite mit einem Standort spezifisch ist. Weitere Informationen [SharePoint Seitentypen](http://go.microsoft.com/fwlink/?LinkID=211584).

 Standardmäßig sind die meisten Seiten, die angezeigt werden, bei der Erstellung einer SharePoint-Websites Websiteseiten. Eine Seite "Website" kann in einer SharePoint-Seite-Bibliothek hinzugefügt werden. Benutzer können eine Websiteseite mit Tools wie SharePoint Designer anpassen. Eine Seite "Website" kann auch Features wie dynamisches Webparts und Webpartzonen hosten.

 Anwendungsseiten nicht möglich. Eine Anwendungsseite ist jedoch die beste Seite erstellen, wenn Sie die benutzerdefinierten Code enthalten soll. Obwohl Sie benutzerdefinierten Code auf einer Webseite hinzufügen können, beendet der Code ausgeführt, wenn der Benutzer die Seite mit Tools wie SharePoint Designer anpasst.

> [!NOTE]
>  Visual Studio bietet keine Vorlagen, mit denen Sie Seiten der Website für eine SharePoint-Website zu erstellen. Weitere Informationen finden Sie unter [SharePoint Seitentypen](http://go.microsoft.com/fwlink/?LinkID=211584).

## <a name="create-an-application-page"></a>Erstellen einer Anwendungsseite
 Fügen Sie zum Erstellen einer Anwendungsseite einer **Anwendungsseite** einem SharePoint-Projekt. Wenn Sie eine Anwendungsseite erstellen, fügt Visual Studio die folgenden Ordner zu Ihrem Projekt hinzu:

|Ordner|Beschreibung|
|------------|-----------------|
|Layouts|Wird das virtuelle _layouts-Verzeichnis des SharePoint-Dateisystems.|
|Unterordner Layouts|Enthält die Dateien, aus denen die Seite "Anwendung" besteht. Standardmäßig hat dieser Ordner den gleichen Namen wie Ihr Projekt. Sie können diesen Ordner zu einem beliebigen Zeitpunkt umbenennen. Wenn Sie das Projekt ausführen, stellt Visual Studio in diesem Ordner mit dem virtuellen _layouts-Verzeichnis des Dateisystems SharePoint bereit.|

 Visual Studio fügt die folgenden Dateien zu Ihrem Projekt hinzu:

|Datei|Beschreibung|
|----------|-----------------|
|Auslagerungsdatei für ASP.NET (*aspx*)|Enthält die XML-Markup, das die Seite definiert.|
|Die Codedatei Anwendungsseite|Enthält Code hinter der Seite "Anwendung". Fügen Sie Code, der Ereignisse in dieser Datei verarbeitet.|
|Application Designer Codedatei|Enthält Code, der vom Designer generiert wird. Bearbeiten Sie diese Datei nicht direkt.|

## <a name="design-and-debug-an-application-page"></a>Entwerfen Sie und Debuggen Sie eine Anwendungsseite
 Entwerfen Sie den Inhalt der Seite für eine Anwendung, indem Sie mit dem Ansicht-Designers in Visual Studio. Dieser Designer wird angezeigt, wenn Sie die Seite "Anwendung" in Ihrem Projekt öffnen (indem Sie darauf doppelklicken oder indem Sie das Kontextmenü öffnen und dann auf **öffnen**) und wählen Sie dann die **Entwurf** Schaltfläche am unteren Rand der Editor.

> [!NOTE]
>  Sie können die Seite entwerfen nur in der **Quelle** Ansicht des Designers. Die **Entwurf** Ansicht des Designers für Anwendungsseiten deaktiviert ist.

 Sie können eine Anwendungsseite Debuggen, ebenso wie Sie andere SharePoint-Projektelemente in Visual Studio debuggen. Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.

 Um die Seite "Anwendung" anzuzeigen, müssen Sie manuell auf den Speicherort der Anwendungsseite navigieren (z. B.: http://<em>Server_Name</em>/_layouts /*Project_Name*  /ApplicationPage1.aspx).

 Weitere Informationen zum Debuggen von SharePoint-Projekte finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Wählen Sie eine Masterseite
 Standardmäßig eine **Anwendungsseite** Element verweist auf die Masterseite der Website, die Sie verwenden, um das Debuggen des Projekts. Seite heißt v4.master und finden Sie im Installationsprogramm die **Masterseitenkatalog** der SharePoint-Website.

 Sie können explizit ändern, die Masterseite von der Anwendungsseite verwendet wird, durch Festlegen der `MasterPageFile` Attribut der Anwendung `Page` Element. (Z. B.: `MasterPageFile="~/_layouts/applicationv4.master"`). In der Tat müssen Sie dieses Attribut festlegen, wenn dynamisch auf der SharePoint-Server nicht aktiviert sind. Weitere Informationen über Masterseiten in SharePoint finden Sie unter [Masterseiten](http://go.microsoft.com/fwlink/?LinkID=169281).

## <a name="see-also"></a>Siehe auch
- [SharePoint Foundation-Entwicklung im Detail](http://go.microsoft.com/fwlink/?LinkID=182103)
- [Übersicht über ASP.NET](/aspnet/overview)
- [ASP.NET-Webseiten 2](/aspnet/web-pages/index)

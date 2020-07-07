---
title: Erstellen von wiederverwendbaren Steuerelementen für Webparts-oder Anwendungs Seiten | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b174e1e16802838f19cec6dce727ea3199df730f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015147"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungs Seiten
  In Visual Studio können Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungs Seiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden. Diese Steuerelemente werden als Benutzer Steuerelemente bezeichnet. Ein Benutzer Steuerelement ist ein zusammengesetztes Steuerelement, das ähnlich wie eine ASP.NET-Webseite funktioniert – Sie können einem Benutzer Steuerelement vorhandene Webserver-Steuerelemente und Markup hinzufügen und Eigenschaften und Methoden für das Steuerelement definieren. Sie können Sie dann in ASP.NET-Webseiten einbetten, wo Sie als Einheit fungieren.

## <a name="create-a-user-control"></a>Erstellen eines Benutzer Steuer Elements
 Fügen Sie ein **Benutzer Steuer** Element zu einem **leeren SharePoint-Projekt**hinzu, um ein Benutzer Steuerelement zu erstellen. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines Benutzer Steuer Elements für eine SharePoint-Anwendungsseite oder ein Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Wenn Sie ein **Benutzer Steuer** Element hinzufügen, erstellt Visual Studio einen Ordner in Ihrem Projekt und fügt dann dem Ordner mehrere Dateien hinzu. In der folgenden Tabelle werden die einzelnen Dateien beschrieben.

|Datei|BESCHREIBUNG|
|----------|-----------------|
|Benutzer Steuerelement-Datei|Definiert das Benutzer Steuerelement. Entwerfen Sie das Benutzer Steuerelement durch Hinzufügen von Steuerelementen und Markup zu dieser Datei.|
|Codedatei|Enthält Code hinter dem Benutzer Steuerelement. Fügen Sie Code zum Behandeln von Ereignissen zu dieser Datei hinzu.|
|Designer-Codedatei|Enthält vom Designer generierte Code und sollte nicht direkt bearbeitet werden.|

## <a name="design-the-user-control"></a>Entwerfen des Benutzer Steuer Elements
 Entwerfen Sie das Benutzer Steuerelement mithilfe des Visual Web Developer-Designers in Visual Studio. Dieser Designer wird angezeigt, wenn Sie die Benutzer Steuerelement Datei in Ihrem Projekt öffnen und die Registerkarte **Entwurf** auswählen.

## <a name="consume-the-user-control"></a>Verwenden des Benutzer Steuer Elements
 Benutzer Steuerelemente werden nicht in SharePoint angezeigt, bis Sie Sie in einer Anwendungsseite oder einem Webpart einschließen.

 Wenn Sie ein Benutzer Steuerelement auf einer Anwendungsseite einschließen möchten, öffnen Sie die Webseite, der Sie das ASP.NET-Benutzer Steuerelement hinzufügen möchten. Wechseln Sie zu Designansicht, wählen Sie dann die benutzerdefinierte Benutzer Steuerelement Datei in Projektmappen-Explorer aus, und ziehen Sie Sie auf die Seite. Das Benutzer Steuerelement ASP.net wird der Seite hinzugefügt, und der Designer erstellt die @ Register-Direktive, die erforderlich ist, damit die Seite das Benutzer Steuerelement erkennt. Sie können jetzt mit den öffentlichen Eigenschaften und Methoden des Steuer Elements arbeiten.

 Wenn Sie ein Benutzer Steuerelement in ein Webpart einschließen möchten, fügen Sie das Benutzer Steuerelement der webpartauflistung <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> in der webpartcodedatei hinzu. Im folgenden Beispiel wird der-Auflistung eines Webparts ein Benutzer Steuerelement hinzugefügt <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> .

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>Debuggen eines Benutzer Steuer Elements
 Stellen Sie zum Debuggen eines Benutzer Steuer Elements sicher, dass das Benutzer Steuerelement in einer Anwendungsseite oder einem Webpart in Ihrem SharePoint-Projekt enthalten ist. Sie können dann Code im Benutzer Steuerelement genauso Debuggen, wie Sie Code in einem beliebigen Visual Studio-Projekt Debuggen.

 Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.

 Öffnen Sie in SharePoint die Anwendungsseite, die das Benutzer Steuerelement enthält. Wenn das Benutzer Steuerelement in einem Webpart enthalten ist, fügen Sie das Webpart einer Webpartseite in SharePoint hinzu.

 Weitere Informationen zum Debuggen von SharePoint-Projekten finden Sie unter Problembehandlung bei [SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Gewusst wie: Erstellen eines Benutzer Steuer Elements für eine SharePoint-Anwendungsseite oder ein Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Zeigt, wie benutzerdefinierte, wiederverwendbare Steuerelemente erstellt werden, die von Anwendungs Seiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden.|

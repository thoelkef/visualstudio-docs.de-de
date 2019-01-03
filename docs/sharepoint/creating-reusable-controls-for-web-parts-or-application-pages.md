---
title: Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d042c42bae59c6dbf92f0e381444cc011b40db0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842818"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten
  In Visual Studio können Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts, die in SharePoint ausgeführt genutzt werden können. Diese Steuerelemente werden als Benutzersteuerelemente bezeichnet. Ein Benutzersteuerelement ist eine Art von Benutzersteuerelement, das ähnlich wie einer ASP.NET-Webseite funktioniert – Sie können vorhandene Webserver-Steuerelemente und Markup zu einem Benutzersteuerelement hinzufügen und Definieren von Eigenschaften und Methoden für das Steuerelement. Anschließend können Sie sie in ASP.NET Webseiten einbetten, in denen sie als Einheit fungieren.  
  
## <a name="create-a-user-control"></a>Erstellen eines Benutzersteuerelements
 Um ein Benutzersteuerelement zu erstellen, fügen Sie eine **Benutzersteuerelement** auf eine **leeres SharePoint-Projekt**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendung Seite oder eine Webpartseite](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Beim Hinzufügen einer **Benutzersteuerelement** , Visual Studio erstellt einen Ordner in Ihrem Projekt, und klicken Sie dann den Ordner mehrere Dateien hinzugefügt. In der folgenden Tabelle werden die einzelnen Dateien beschrieben.  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|Benutzersteuerelement-Datei|Definiert das Benutzersteuerelement. Entwerfen Sie das Benutzersteuerelement, durch das Hinzufügen von Steuerelementen und das Markup für diese Datei.|  
|Codedatei|Enthält Code hinter das Benutzersteuerelement. Fügen Sie Code zum Verarbeiten von Ereignissen für diese Datei.|  
|Designer-Codedatei|Enthält Code, die vom Designer generiert und sollte nicht direkt bearbeitet werden.|  
  
## <a name="design-the-user-control"></a>Entwerfen des Benutzersteuerelements
 Entwerfen Sie das Benutzersteuerelement, indem Sie mit dem Visual Web Developer-Designer in Visual Studio. Dieser Designer wird angezeigt, wenn Sie die Benutzersteuerelement-Datei in Ihrem Projekt zu öffnen, und wählen Sie die **Entwurf** Registerkarte.  

## <a name="consume-the-user-control"></a>Das Benutzersteuerelement verwenden
 Steuerelemente werden nicht in SharePoint angezeigt, bis Sie sie in einer Anwendungsseite oder ein Webpart einschließen.  
  
 Um ein Steuerelement auf einer Anwendungsseite einzuschließen, öffnen Sie die Webseite, die Sie das ASP.NET-Benutzersteuerelement hinzufügen möchten. Wechseln Sie zur Entwurfsansicht wechseln, und wählen Sie Ihr benutzerdefiniertes Benutzersteuerelement-Datei im Projektmappen-Explorer, und ziehen Sie sie auf der Seite. Das Benutzersteuerelement von ASP.NET wird auf der Seite hinzugefügt, und der Designer erstellt, die @ Register-Direktive, die für die Seite, um das Steuerelement erkennt erforderlich ist. Sie können jetzt mit öffentlichen Eigenschaften und Methoden des Steuerelements arbeiten.  
  
 Wenn ein Benutzersteuerelement in einem Webpart einschließen möchten, fügen Sie das Benutzersteuerelement zum Webpart <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> Auflistung in der Webpart-Codedatei. Im folgenden Beispiel wird ein Benutzersteuerelement, um die <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> Auflistung eines Webparts.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>Debuggen Sie ein Benutzersteuerelement
 Um ein Benutzersteuerelement zu debuggen, stellen Sie sicher, dass das Benutzersteuerelement in einer Anwendungsseite oder ein Webpart in Ihrer SharePoint-Projekt enthalten ist. Sie können Code in das Benutzersteuerelement dann Debuggen, ebenso wie Sie Code in jedem Visual Studio-Projekt debuggen.  
  
 Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.  
  
 Öffnen Sie die Seite "Anwendung", die das Benutzersteuerelement enthält, in SharePoint. Wenn das Benutzersteuerelement in einem Webpart enthalten ist, fügen Sie das Webpart zu einer Webparts-Seite in SharePoint hinzu.  
  
 Weitere Informationen zum Debuggen von SharePoint-Projekte finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Verwandte Themen
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendung Seite oder eine Webpartseite](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Erfahren Sie, wie Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts, die in SharePoint ausgeführt genutzt werden können.|  

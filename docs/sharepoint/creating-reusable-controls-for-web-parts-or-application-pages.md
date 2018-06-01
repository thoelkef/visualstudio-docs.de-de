---
title: Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten | Microsoft Docs
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
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47a519db245e2ec15548ba1d46a583d0a73f466f
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693483"
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten
  In Visual Studio können Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts, die in SharePoint ausgeführt genutzt werden können. Diese Steuerelemente werden als Benutzersteuerelemente bezeichnet. Ein Benutzersteuerelement ist eine Art von zusammengesetzten Steuerelementen, die ähnlich wie eine ASP.NET-Webseite funktioniert – Sie können vorhandene Webserversteuerelemente und Markup in einem Benutzersteuerelement hinzufügen und Eigenschaften und Methoden für das Steuerelement definieren. Anschließend können Sie sie in ASP.NET Web Pages einbetten, in dem sie als Einheit handeln.  
  
## <a name="create-a-user-control"></a>Erstellen eines Benutzersteuerelements
 Um ein benutzerdefiniertes Steuerelement zu erstellen, fügen einen **Benutzersteuerelement** auf eine **leeres SharePoint-Projekt**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Beim Hinzufügen einer **Benutzersteuerelement** item, Visual Studio erstellt einen Ordner in Ihrem Projekt, und klicken Sie dann den Ordner mehrere Dateien hinzugefügt. In der folgenden Tabelle werden die einzelnen Dateien beschrieben.  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|Benutzersteuerelementdatei|Definiert das Benutzersteuerelement. Entwerfen Sie das Benutzersteuerelement durch Hinzufügen von Steuerelementen und Markup in dieser Datei.|  
|Codedatei|Enthält Code hinter das Benutzersteuerelement. Fügen Sie Code zum Verarbeiten von Ereignissen in dieser Datei.|  
|Designer-Codedatei|Enthält die vom Designer generierten Code und sollte nicht direkt bearbeitet werden.|  
  
## <a name="design-the-user-control"></a>Entwerfen des Benutzersteuerelements
 Entwerfen Sie das Benutzersteuerelement mit dem Visual Web Developer-Designer in Visual Studio. Dieser Designer wird angezeigt, wenn Sie die Benutzersteuerelementdatei in Ihrem Projekt zu öffnen, und wählen Sie die **Entwurf** Registerkarte.  

## <a name="consume-the-user-control"></a>Das Benutzersteuerelement verwenden
 Benutzersteuerelemente werden nicht in SharePoint angezeigt, bis Sie sie in einer Anwendungsseite oder ein Webpart einschließen.  
  
 Um ein benutzerdefiniertes Steuerelement auf einer Anwendungsseite einzuschließen, öffnen Sie die Webseite, die Sie das Benutzersteuerelement ASP.NET hinzufügen möchten. Wechseln Sie zur Entwurfsansicht, und klicken Sie dann wählen Sie Ihre benutzerdefinierte Benutzersteuerelementdatei im Projektmappen-Explorer, und ziehen Sie sie auf der Seite. Das Benutzersteuerelement ASP.NET wird auf der Seite hinzugefügt und erstellt der Designer die @ Register-Direktive, die für die Seite erkennt das Benutzersteuerelement erforderlich ist. Sie können jetzt mit öffentlichen Eigenschaften und Methoden des Steuerelements arbeiten.  
  
 Um ein Benutzersteuerelement in ein Webpart einzuschließen, fügen Sie das Benutzersteuerelement zum Webpart <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> Auflistung in der Codedatei-Webpart. Im folgenden Beispiel wird ein benutzerdefiniertes Steuerelement an die <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> Auflistung eines Webparts.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>Debuggen Sie ein benutzerdefiniertes Steuerelement
 Um ein benutzerdefiniertes Steuerelement zu debuggen, stellen Sie sicher, dass das Benutzersteuerelement in einem Webpart oder einer Seite "Anwendung" in das SharePoint-Projekt enthalten ist. Sie können Code im Benutzersteuerelement dann Debuggen, ebenso wie Sie Code in jedem Visual Studio-Projekt debuggen.  
  
 Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.  
  
 Öffnen Sie die Seite "Anwendung", die das Benutzersteuerelement enthält, in SharePoint. Wenn das Benutzersteuerelement in einem Webpart enthalten ist, können fügen Sie das Webpart einer Webpartseite in SharePoint hinzu.  
  
 Weitere Informationen zum Debuggen von SharePoint-Projekte finden Sie unter [SharePoint-Lösungen zur Problembehandlung](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Verwandte Themen
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Zeigt, wie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts, die in SharePoint ausgeführt genutzt werden können.|  
  
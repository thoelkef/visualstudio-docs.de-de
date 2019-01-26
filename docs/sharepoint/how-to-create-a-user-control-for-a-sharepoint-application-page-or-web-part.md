---
title: 'Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder -Webpart | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58288f482b7b32319d8c45c9b12e75899541b81e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865046"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendung Seite oder eine Webpartseite
  Sie können benutzerdefinierte Benutzersteuerelemente erstellen, die benutzerdefinierte Funktionalität für die SharePoint-Lösung bereitstellen, und Sie können diese Funktion im Projekt wiederverwenden. Sie können die Benutzersteuerelemente in einem Webpart oder einer Anwendungsseite verwenden, weitere ASP.NET- und SharePoint-Steuerelemente hinzufügen und Eigenschaften sowie Methoden für das Steuerelement definieren. Weitere Informationen zu Benutzersteuerelementen finden Sie unter [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) und [Benutzersteuerelementen und Serversteuerelementen in SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>So erstellen Sie ein Benutzersteuerelement für SharePoint  
  
1.  Öffnen oder erstellen Sie in Visual Studio ein SharePoint-Projekt.  
  
     Finden Sie unter [SharePoint-Projekt und Projekt Elementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.  
  
3.  Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
4.  In der **installiert** Bereich, wählen Sie die **Office/SharePoint** Knoten.  
  
5.  Wählen Sie in der Liste der SharePoint-Vorlagen, **Benutzersteuerelement (nur Farmlösung)**.  
  
    > [!NOTE]  
    >  Benutzersteuerelemente funktionieren nur in Farmlösungen.  
  
6.  In der **Namen** Feld Geben Sie einen Namen für das Benutzersteuerelement, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Visual Studio fügt dem Projekt mehrere Ordner und Dateien hinzu. Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Standardmäßig wird die Benutzersteuerelement-Datei in die **Quelle** Sicht des Visual Web Developer-Designers. In dieser Ansicht können Sie das XML-Markup des Steuerelements bearbeiten. Sie können zum wechseln **Entwurf** anzeigen, sollten Sie das Steuerelement visuell zu entwerfen, ziehen Sie Steuerelemente aus der **Toolbox**. Finden Sie unter [Entwurfsansicht, Webseiten-Designer](/previous-versions/aspnet/ms178149\(v\=vs.100\)).  
  
7.  Wenn Sie Ereignisse behandeln, die im Steuerelement auftreten, fügen Sie der Codedatei des Benutzersteuerelements Code hinzu.  
  
     Diese Datei wird im **Projektmappen-Explorer** unter der Benutzersteuerelementdatei und verfügt über eine *cs* oder *vb* Erweiterung, abhängig von der Sprache des Projekts.  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  

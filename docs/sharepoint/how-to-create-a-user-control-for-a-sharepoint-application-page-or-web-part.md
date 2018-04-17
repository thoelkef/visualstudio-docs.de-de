---
title: 'Vorgehensweise: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder Webpart | Microsoft Docs'
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
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 26f71486f48379f0f7005107b3df4f9f79960ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Gewusst wie: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart
  Sie können benutzerdefinierte Benutzersteuerelemente erstellen, die benutzerdefinierte Funktionalität für die SharePoint-Lösung bereitstellen, und Sie können diese Funktion im Projekt wiederverwenden. Sie können die Benutzersteuerelemente in einem Webpart oder einer Anwendungsseite verwenden, weitere ASP.NET- und SharePoint-Steuerelemente hinzufügen und Eigenschaften sowie Methoden für das Steuerelement definieren. Weitere Informationen zu Benutzersteuerelemente, finden Sie unter [Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) und [Benutzersteuerelemente und Serversteuerelementen in SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>So erstellen Sie ein Benutzersteuerelement für SharePoint  
  
1.  Öffnen oder erstellen Sie in Visual Studio ein SharePoint-Projekt.  
  
     Finden Sie unter [SharePoint-Projekt und Projekt Elementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.  
  
3.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
4.  In der **installiert** Bereich, wählen Sie die **Office/SharePoint** Knoten.  
  
5.  Wählen Sie in der Liste der SharePoint-Vorlagen **Benutzersteuerelement (nur Farmlösung)**.  
  
    > [!NOTE]  
    >  Benutzersteuerelemente funktionieren nur in Farmlösungen.  
  
6.  In der **Namen** Feld Geben Sie einen Namen für das Benutzersteuerelement, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Visual Studio fügt dem Projekt mehrere Ordner und Dateien hinzu. Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Wird standardmäßig die Benutzersteuerelementdatei angezeigt wird, der **Quelle** Ansicht des Visual Web Developer-Designers. In dieser Ansicht können Sie das XML-Markup des Steuerelements bearbeiten. Sie können zum wechseln **Entwurf** anzeigen, wenn Sie das Steuerelement durch Ziehen von Steuerelementen von visuell zu entwerfen möchten die **Toolbox**. Finden Sie unter [Entwurfsansicht, Webseiten-Designer](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Wenn Sie Ereignisse behandeln, die im Steuerelement auftreten, fügen Sie der Codedatei des Benutzersteuerelements Code hinzu.  
  
     Diese Datei wird im **Projektmappen-Explorer** unter der Benutzersteuerelementdatei und verfügt über eine Erweiterung .cs oder .vb abhängig von der Sprache des Projekts.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  
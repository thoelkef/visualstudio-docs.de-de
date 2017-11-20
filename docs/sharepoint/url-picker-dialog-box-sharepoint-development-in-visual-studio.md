---
title: URL-Auswahldialogfeld (SharePoint-Entwicklung in Visual Studio) | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c97bd5e6fb9ad320a9f353eaa67114931a0d1b54
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL-Auswahldialogfeld (SharePoint-Entwicklung in Visual Studio)
  Klicken Sie im Dialogfeld Auswahl der URL können Sie auswählen, Dateien, z. B. master Auslagerungsdateien oder Image-Dateien befinden sich im Projekt oder auf dem lokalen Server, auf dem SharePoint ausgeführt wird.  
  
 Dieses Dialogfeld wird angezeigt, wenn Sie die Option aus, um eine Datei auszuwählen und eine Eigenschaft festgelegt haben. Sie können dieses Dialogfeld öffnen, indem Sie dann die Schaltfläche mit den Auslassungspunkten (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) neben verschiedener Eigenschaften in der **Eigenschaften** Fenster. Schaltfläche mit den Auslassungspunkten auch wird als eine von IntelliSense Prompt bei der Zuweisung von Werten für bestimmte Attribute in der **Quelle** Ansicht des Designers.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Projektordner**  
 Zeigt eine Liste der Ordner im Projekt oder auf dem lokalen Server, auf dem SharePoint ausgeführt wird, definiert. Wählen Sie die Erweiterungsschaltfläche, um die Unterordner anzuzeigen.  
  
 Erweitern Sie die **Projekt** Knoten Dateien im Projekt wählen. Um das Dialogfeld ausgewählt werden können, müssen die Dateien in Ihrem Projekt die folgenden Kriterien erfüllen:  
  
-   Die Datei muss in einen zugeordneten Ordner befinden.  
  
-   Das Lösungspaket muss die Datei hinzugefügt werden.  
  
-   Die Datei kann nicht in einem anderen Projekt befinden.  
  
 Wenn Sie möchten die Dateien zu verweisen, die diese Kriterien nicht erfüllen, müssen Sie den Pfad der Datei manuell eingeben.  
  
 Erweitern Sie die **Server** Knoten, um Dateien auszuwählen, die auf dem lokalen Server befinden, auf dem SharePoint ausgeführt wird. Um das Dialogfeld ausgewählt werden können, müssen diese Dateien die folgenden Kriterien erfüllen:  
  
-   Die Datei muss in einem der folgenden zugeordneten Ordner befinden: **Bilder**, **Layouts**, oder **ControlTemplates**.  
  
-   Die Datei kann nicht in der SharePoint-Inhaltsdatenbank gespeichert sein.  
  
 Wenn Sie möchten die Dateien zu verweisen, die diese Kriterien nicht erfüllen, müssen Sie den Pfad der Datei manuell eingeben.  
  
 **Inhalt des Ordners**  
 Zeigt eine Liste mit den Dateien des ausgewählten Ordners an. Wählen Sie eine Datei, und wählen Sie dann die **OK** Schaltfläche, um das Dialogfeld zu schließen, und senden Ihre Auswahl an den Prozess, die diese aufgerufen.  
  
 **Dateityp**  
 Können Sie eine Liste der Dateien auswählen, die für den Task geeignet sind, die Sie ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
  
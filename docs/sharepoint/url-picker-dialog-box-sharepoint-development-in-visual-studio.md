---
title: URL-Auswahldialogfeld (SharePoint-Entwicklung in Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c890d1cd1acfa0acc5a28c6418dbd961f795107e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
  
  
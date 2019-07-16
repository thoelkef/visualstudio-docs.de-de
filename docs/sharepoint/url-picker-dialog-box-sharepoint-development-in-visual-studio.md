---
title: URL-Auswahldialogfeld (SharePoint-Entwicklung)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 991693c3379e008a2a907efd3127290c7e804c22
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261942"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL-Auswahldialogfeld (SharePoint-Entwicklung in Visual Studio)
  Sie können Dateien wie z. B. Masterseitendateien oder Imagedateien, die sich in Ihrem Projekt oder auf dem lokalen Server, auf dem SharePoint ausgeführt wird, klicken Sie im Dialogfeld URL-Auswahl.

 Dieses Dialogfeld wird angezeigt, wenn Sie die Option zum Auswählen einer Datei, eine Eigenschaft festzulegen. Sie können dieses Dialogfeld öffnen, indem Sie dann die Schaltfläche mit den Auslassungspunkten (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) neben verschiedener Eigenschaften in der **Eigenschaften** Fenster. Schaltfläche mit den Auslassungspunkten auch angezeigt, wie eine von IntelliSense Eingabeaufforderung Wenn Sie bestimmte Attribute in Werte zuweisen der **Quelle** Ansicht des Designers.

## <a name="uielement-list"></a>UIElement-Liste
 **-Projektordner** zeigt eine Liste der Ordner definiert, in das Projekt oder auf dem lokalen Server, auf dem SharePoint ausgeführt wird. Wählen Sie die Schaltfläche "Erweiterung", um die Unterordner anzuzeigen.

 Erweitern Sie die **Projekt** Knoten aus, um die Dateien in Ihrem Projekt zu wählen. Um das Dialogfeld ausgewählt werden können, müssen die Dateien in Ihrem Projekt die folgenden Kriterien erfüllen:

- Die Datei muss in einen zugeordneten Ordner befinden.

- Die Datei muss dem Lösungspaket hinzugefügt werden.

- Die Datei kann nicht in einem anderen Projekt befinden.

  Wenn Sie möchten die Dateien zu verweisen, die diese Kriterien nicht erfüllen, müssen Sie den Pfad der Datei manuell eingeben.

  Erweitern Sie die **Server** Knoten aus, um die Dateien auswählen, die auf dem lokalen Server befinden, auf dem SharePoint ausgeführt wird. Um das Dialogfeld ausgewählt werden können, müssen diese Dateien die folgenden Kriterien erfüllen:

- Die Datei muss in einem der folgenden zugeordneten Ordner befinden: **Images**, **Layouts**, oder **ControlTemplates**.

- Die Datei kann nicht in der SharePoint-Inhaltsdatenbank befinden.

  Wenn Sie möchten die Dateien zu verweisen, die diese Kriterien nicht erfüllen, müssen Sie den Pfad der Datei manuell eingeben.

  **Inhalt des Ordners** zeigt eine Liste der Dateien im ausgewählten Ordner. Wählen Sie eine Datei, und wählen Sie dann die **OK** Schaltfläche, um das Dialogfeld zu schließen, und senden Ihre Auswahl an den Prozess, die diese aufgerufen.

  **Dateityp** können Sie aus einer Liste von Dateien auswählen, die Sie ausführen für die Aufgabe geeignet sind.

## <a name="see-also"></a>Siehe auch
- [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

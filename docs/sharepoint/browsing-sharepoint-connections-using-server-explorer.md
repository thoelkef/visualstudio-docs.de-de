---
title: Durchsuchen von SharePoint-Verbindungen mithilfe von Server-Explorer | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3804b97967cffb299393e7e3a8866e51a2e3224
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931358"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Durchsuchen von SharePoint-Verbindungen mithilfe von Server-Explorer
  Jetzt können Sie lokale SharePoint-Verbindungen in Durchsuchen **Server-Explorer**. Mit diesem Verfahren können Sie auf Ihrem System durch die Komponenten einer SharePoint-Website navigieren. SharePoint-Site-Komponenten, z. B. Listendefinitionen und Inhaltstypen, angezeigt in einem Knoten mit dem Namen **SharePoint-Verbindungen** in der Strukturansicht des **Server-Explorer**. Anzuzeigende **Server-Explorer**, wählen Sie auf der Menüleiste **Ansicht** > **Server-Explorer**. Zusätzlich zur Anzeige der SharePoint-Site-Komponenten, können Sie Elemente entfernen, deren Eigenschaften anzeigen oder Aktualisieren mithilfe der Befehle im Kontextmenü der Strukturansicht.  
  
> [!IMPORTANT]  
>  Um einer SharePoint-Website zu durchsuchen, müssen Sie Administrator der SharePoint-Websitesammlung sein, und Sie werden Sie als Administrator des lokalen Computers müssen Visual Studio ausführen. Andernfalls die Website wird in **Server-Explorer**, aber Sie können nicht den Knoten erweitern. Öffnen Sie die Website in einem Webbrowser öffnen, um zu überprüfen, ob Sie ein Administrator der Websitesammlung sind, die **Websiteaktionen** Menü wählen **Websiteberechtigungen**, und klicken Sie auf die **Berechtigungen: Teamwebsite** Seite die **Websitesammlungsadministratoren** Befehl die **verwalten** -Gruppe auf dem Menüband. Ihr Name wird im Textfeld angezeigt, wenn Sie Administrator einer Websitesammlung sind. Wenn die **Websitesammlungsadministratoren** Befehl nicht in der Gruppe "verwalten" auf dem Menüband angezeigt wird, Sie sind ein Administrator für die Websitesammlung nicht und die entsprechenden Berechtigungen müssen vom Administrator Website abrufen.  
  
## <a name="server-explorer-nodes"></a>Server-Explorer-Knoten
 Jede Komponente von einer SharePoint-Website wird dargestellt, durch einen Knoten in der **Server-Explorer** Strukturansicht unter **SharePoint-Verbindungen**. Standard-SharePoint-Websites enthalten z. B. einen Inhaltstyp namens-Lösung, die einen Diskussionstyp, der darstellt in zeigt die **Diskussionen** auf der Seite der SharePoint-Website. Der Inhaltstyp Diskussion enthält mehrere Felder. An diese Felder in **Server-Explorer**, erweitern Sie die **"ContentTypes"** Knoten, und klicken Sie dann die **Diskussion** Knoten. Darunter befinden sich mehrere Feldknoten, z. B. Text, Betreff der Diskussion und Titel.  
  
## <a name="node-shortcut-menu-commands"></a>Knoten: Kontextmenübefehle
 Jeder Knoten verfügt über ein Kontextmenü aufrufen, die Sie zugreifen, indem Sie mit der rechten Maustaste des Knotens, oder Sie ihn auswählen, und wählen Sie dann die **UMSCHALT**+**F10** Schlüssel. Node-Befehle können Folgendes umfassen:  
  
|Befehlsname|Beschreibung|  
|------------------|-----------------|  
|Aktualisieren|Aktualisiert die Strukturansicht, um Änderungen widerzuspiegeln, die seit dem letzten möglicherweise aufgetreten, die der Knoten angezeigt wurde.|  
|Löschen|Entfernt den ausgewählten Knoten in der Strukturansicht. **Hinweis**:  Mit diesem Befehl ist aktiviert, nur auf SharePoint-Verbindungen aufgeführt, unter dem **SharePoint-Verbindungen** Knoten.|  
|Eigenschaften|Zeigt die verfügbaren Eigenschaften für den ausgewählten Knoten in der **Eigenschaften** Fenster. Die Eigenschaften sind alle schreibgeschützt, und nicht jeder Knoten verfügt über Eigenschaften zugeordnet.|  
|Verbindung hinzufügen|Ermöglicht Ihnen die Angabe eine SharePoint-Website, die Sie durchsuchen möchten. Auf der **SharePoint-Verbindungen** und Unterwebsite-Knoten.|  
|In Browser anzeigen|Zeigt die ausgewählte Liste in einem Webbrowser. Mit diesem Befehl steht für einige Listen unter der **listet** Knoten, der in enthalten ist **Listen und Bibliotheken**.|  
  
## <a name="related-topics"></a>Verwandte Themen
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Hinzufügen oder Entfernen von SharePoint-Verbindungen](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Beschreibt die erforderlichen Schritte zum Hinzufügen einer neuen SharePoint-Website auf der **SharePoint-Verbindungen** Knoten **Server-Explorer**.|  
  
## <a name="see-also"></a>Siehe auch
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)  

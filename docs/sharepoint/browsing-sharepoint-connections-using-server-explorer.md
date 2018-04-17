---
title: Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: ca6e7ff8d046ae94d6016c01b346bce592b2fcf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="browsing-sharepoint-connections-using-server-explorer"></a>Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer
  Sie können lokale SharePoint-Verbindungen in Durchsuchen **Server-Explorer**. Mithilfe dieser Technik können Sie auf Ihrem System durch die Komponenten einer SharePoint-Website navigieren. SharePoint-Website-Komponenten, z. B. Listendefinitionen und Inhaltstypen, angezeigt werden, in einem Knoten mit dem Namen **SharePoint-Verbindungen** in der Strukturansicht des **Server-Explorer**. Anzuzeigende **Server-Explorer**, wählen Sie in der Menüleiste **Ansicht**, **Server-Explorer**. Zusätzlich zur Anzeige der SharePoint-Website-Komponenten, Sie Entfernen von Elementen, zugehörigen Eigenschaften anzeigen oder Aktualisieren mithilfe von Befehlen im Kontextmenü die Strukturansicht.  
  
> [!IMPORTANT]  
>  Informationen zum Durchsuchen einer SharePoint-Websites müssen Sie Administrator der SharePoint-Websitesammlung sein, und sein muss Visual Studio als Administrator des lokalen Computers ausgeführt. Andernfalls wird der Standort im **Server-Explorer**, aber Sie können nicht den Knoten erweitern. Öffnen Sie die Website in einem Webbrowser öffnen, um zu überprüfen, ob Sie einen Administrator der Websitesammlung, die **Websiteaktionen** Menü Wählen Sie **Websiteberechtigungen**, und klicken Sie auf die **Berechtigungen: Team Standort** Seite, und wählen Sie die **Websitesammlungs-Administratoren** Befehl die **verwalten** Gruppe auf dem Menüband. Der Name wird im Textfeld angezeigt, wenn Sie Administrator einer Websitesammlung sind. Wenn die **Websitesammlungs-Administratoren** Befehl nicht in der Gruppe verwalten, auf dem Menüband angezeigt wird, Sie sind kein Administrator für die Websitesammlung nicht und Sie benötigen die entsprechenden Berechtigungen vom Administrator Standorts.  
  
## <a name="server-explorer-nodes"></a>Server-Explorer-Knoten  
 Jede Komponente einer SharePoint-Website wird dargestellt, von einem Knoten in der **Server-Explorer** Strukturansicht unter **SharePoint-Verbindungen**. Standard-SharePoint-Websites umfassen z. B. einen Inhaltstyp namens Diskussion, der einen Diskussionstyp, die darstellt in angezeigt der **Diskussionen** Seite der SharePoint-Website. Der Inhaltstyp Diskussion enthält mehrere Felder. An diesen Feldern in **Server-Explorer**, erweitern Sie die **Inhaltstypen** Knoten, und klicken Sie dann die **Diskussion** Knoten. Unter befinden sich mehrere Feldknoten, z. B. Text, Diskussionsbetreff und Titel.  
  
## <a name="node-shortcut-menu-commands"></a>Kontextmenübefehle für Knoten  
 Jeder Knoten verfügt über ein Kontextmenü aufrufen, die Sie zugreifen, indem Sie mit der rechten Maustaste des Knotens oder es auswählen und dann die Tasten UMSCHALT + F10. Knotenbefehle können Folgendes umfassen:  
  
|Befehlsname|Beschreibung|  
|------------------|-----------------|  
|Aktualisieren|Aktualisiert die Strukturansicht, um Änderungen widerzuspiegeln, die seit der letzten Ausführung möglicherweise aufgetreten Knotens angezeigt wurde.|  
|Löschen|Entfernt den ausgewählten Knoten aus der Strukturansicht angezeigt. **Hinweis:** mit diesem Befehl wird nur für SharePoint-Verbindungen, die unter aufgeführten aktiviert die **SharePoint-Verbindungen** Knoten.|  
|Eigenschaften|Zeigt die verfügbaren Eigenschaften für den ausgewählten Knoten in der **Eigenschaften** Fenster. Die Eigenschaften sind alle schreibgeschützten, und nicht jeder Knoten enthält Eigenschaften zugeordnet.|  
|Verbindung hinzufügen|Ermöglicht Ihnen die Angabe eine SharePoint-Website, die Sie durchsuchen möchten. Über die **SharePoint-Verbindungen** und Unterwebsite Knoten.|  
|In Browser anzeigen|Zeigt die ausgewählte Liste im Webbrowser an. Mit diesem Befehl steht für einige Listen unter der **listet** Knoten im enthalten **Listen und Bibliotheken**.|  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Hinzufügen oder Entfernen von SharePoint-Verbindungen](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Beschreibt die Schritte, die für das Hinzufügen einer neuen SharePoint-Website erforderlich sind die **SharePoint-Verbindungen** Knoten **Server-Explorer**.|  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  
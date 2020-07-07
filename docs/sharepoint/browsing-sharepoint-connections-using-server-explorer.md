---
title: Durchsuchen von SharePoint-Verbindungen mit Server-Explorer | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baf580ace98ab14032de1e9a3edf18af2b2cfee8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016356"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Durchsuchen von SharePoint-Verbindungen mit Server-Explorer
  Sie können jetzt in **Server-Explorer**lokale SharePoint-Verbindungen durchsuchen. Mithilfe dieser Technik können Sie durch die Komponenten einer SharePoint-Website auf Ihrem System navigieren. SharePoint-Website Komponenten, z. b. Listen Definitionen und Inhaltstypen, werden in der Strukturansicht von **Server-Explorer**in einem Knoten mit dem Namen **SharePoint-Verbindungen** angezeigt. Um **Server-Explorer**anzuzeigen, wählen Sie in der Menüleiste **View**die Option  >  **Server-Explorer**anzeigen aus. Zusätzlich zum Anzeigen der SharePoint-Website Komponenten können Sie Elemente entfernen, ihre Eigenschaften anzeigen oder die Strukturansicht mithilfe der Befehle im Kontextmenü aktualisieren.

> [!IMPORTANT]
> Um eine SharePoint-Website zu durchsuchen, müssen Sie Administrator der SharePoint-Website Sammlung sein, und Sie müssen Visual Studio als Administrator des lokalen Computers ausführen. Andernfalls wird die Site in **Server-Explorer**angezeigt, aber Sie können Ihren Knoten nicht erweitern. Um zu überprüfen, ob Sie ein Administrator der Website Sammlung sind, öffnen Sie die Website in einem Webbrowser, öffnen Sie das Menü " **Website Aktionen** ", wählen Sie " **Website Berechtigungen**" aus, und wählen Sie dann auf der Seite **Berechtigungen: Team Website** den Befehl **Website Sammlungs Administratoren** aus der Gruppe **Verwalten** auf dem Menüband aus. Wenn Sie ein Website Sammlungs Administrator sind, wird Ihr Name im Textfeld angezeigt. Wenn der Befehl " **Website Sammlungs Administratoren** " nicht in der Gruppe "verwalten" auf dem Menüband angezeigt wird, sind Sie kein Administrator für die Website Sammlung, und Sie müssen die entsprechenden Berechtigungen vom Website Administrator erhalten.

## <a name="server-explorer-nodes"></a>Server-Explorer Knoten
 Jede Komponente einer SharePoint-Website wird durch einen Knoten in der **Server-Explorer** Strukturansicht unter **SharePoint-Verbindungen**dargestellt. Standardmäßige SharePoint-Sites enthalten beispielsweise einen Inhaltstyp namens "Diskussion", der einen Diskussions Typ darstellt, der auf der Seite " **Diskussionen** " der SharePoint-Website angezeigt wird. Der Inhaltstyp für die Diskussion enthält mehrere Felder. Um diese Felder in **Server-Explorer**anzuzeigen, erweitern Sie den Knoten **ContentTypes** und dann den Knoten **Erörterung** . Darunter sind mehrere Feld Knoten, z. b. Text, Diskussions Betreff und Titel.

## <a name="node-shortcut-menu-commands"></a>Befehle für Knoten Kontextmenü
 Jeder Knoten verfügt über ein Kontextmenü, auf das Sie zugreifen, indem Sie mit der rechten Maustaste auf den Knoten klicken oder es auswählen und **dann die** + Taste**F10** drücken. Knoten Befehle können Folgendes umfassen:

|Befehlsname|BESCHREIBUNG|
|------------------|-----------------|
|Aktualisieren|Aktualisiert die Strukturansicht, um Änderungen widerzuspiegeln, die möglicherweise seit der letzten Anzeige des Knotens aufgetreten sind.|
|Löschen|Entfernt den ausgewählten Knoten aus der Strukturansicht. **Hinweis:**  Dieser Befehl ist nur für SharePoint-Verbindungen aktiviert, die unter dem Knoten **SharePoint-Verbindungen** aufgelistet sind.|
|Eigenschaften|Zeigt die im **Eigenschaften** Fenster verfügbaren Eigenschaften für den ausgewählten Knoten an. Die Eigenschaften sind schreibgeschützt, und nicht jedem Knoten sind Eigenschaften zugeordnet.|
|Verbindung hinzufügen|Ermöglicht es Ihnen, eine SharePoint-Website anzugeben, die Sie durchsuchen möchten. Verfügbar für den Knoten **SharePoint-Verbindungen** und untergeordnete Knoten.|
|In Browser anzeigen|Zeigt die ausgewählte Liste im Webbrowser an. Dieser Befehl ist in einigen Listen unter dem Knoten " **Listen** " verfügbar, der in **Listen und Bibliotheken**enthalten ist.|

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Vorgehensweise: Hinzufügen oder Entfernen von SharePoint-Verbindungen](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Beschreibt die Schritte, die zum Hinzufügen einer neuen SharePoint-Website zum Knoten **SharePoint-Verbindungen** in **Server-Explorer**erforderlich sind.|

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)

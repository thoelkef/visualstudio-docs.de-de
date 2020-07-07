---
title: Erweitern der SharePoint-Tools in Visual Studio | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dc0cc0d0af73d032d870629877b62c94e6b347b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016032"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Erweitern der SharePoint-Tools in Visual Studio
  Die SharePoint-Tools in Visual Studio erfüllen die Anforderungen vieler Anwendungs Entwicklungsszenarien. Sie können jedoch Fälle ermitteln, in denen Sie keine Funktionen bereitstellen, die Sie oder andere Entwickler benötigen. In diesen Fällen können Sie die SharePoint-Tools erweitern, um die Funktionalität zu erstellen, die Sie benötigen.

## <a name="how-to-extend-the-sharepoint-tools"></a>Erweitern der SharePoint-Tools
 Sie können das SharePoint-Projekt System und den Knoten **SharePoint-Verbindungen** im Fenster **Server-Explorer** erweitern.

### <a name="extend-the-sharepoint-project-system"></a>Erweitern des SharePoint-Projekt Systems
 Visual Studio enthält eine Reihe von Projektvorlagen und Element Vorlagen, die Sie zum Erstellen von SharePoint-Lösungen verwenden können. Beispielsweise sind Vorlagen für Ereignis Empfänger, Listen Definitionen, Workflows und Webparts vorhanden. Sie können jedoch auch eigene Typen von SharePoint-Projekt Elementen zum Erstellen von SharePoint-Komponenten definieren, wie z. b. Felder oder benutzerdefinierte Aktionen. Sie können auch Erweiterungen für SharePoint-Projekt Elementtypen erstellen, die bereits in Visual Studio installiert sind, und Sie können Erweiterungen für SharePoint-Projekte erstellen.

 Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projekt Systems](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Erweitern des Knotens "SharePoint-Verbindungen" in Server-Explorer
 In Visual Studio können Sie den Knoten **SharePoint-Verbindungen** im **Server-Explorer** Fenster verwenden, um viele der Komponenten von einer oder mehreren lokalen SharePoint-Sites in einer hierarchischen Strukturansicht anzuzeigen. Sie können den Knoten **SharePoint-Verbindungen** auch folgendermaßen erweitern:

- Durch das Hinzufügen eigener Knoten. Dies ist hilfreich, wenn Sie Komponenten von SharePoint-Websites anzeigen möchten, die nicht standardmäßig angezeigt werden.

- Durch Erweitern vorhandener Knoten. Beispielsweise können Sie einem vorhandenen Knoten einen neuen untergeordneten Knoten hinzufügen, oder Sie können einem Knoten ein Kontextmenü Element hinzufügen und Aufgaben ausführen, wenn ein Entwickler auf das Menü Element klickt.

  Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungs Knotens in Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Anforderungen an die Entwicklungs Computer
 Zum Erstellen von Erweiterungen für die SharePoint-Tools müssen auf dem Entwicklungs Computer dieselben Anforderungen zum Erstellen von SharePoint-Lösungen in Visual Studio erfüllt werden.

 Außerdem wird empfohlen, das zu installieren [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . Das SDK enthält Projektvorlagen und Tools, mit denen Sie Visual Studio erweitern können. Das SDK enthält eine Projektvorlage, die Sie verwenden können, um problemlos ein Visual Studio-Erweiterungspaket (VSIX) zu erstellen. VSIX-Pakete sind die bevorzugte Methode zum Bereitstellen von Visual Studio-Erweiterungen in Visual Studio. Alle Erweiterungen für SharePoint-Tools müssen mithilfe von VSIX-Paketen bereitgestellt werden. Bei allen exemplarischen Vorgehensweisen in dieser Dokumentation wird davon ausgegangen, dass Sie [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installiert haben.

 Informationen zum Installieren des Visual Studio SDK finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Weitere Informationen zu Visual Studio-Erweiterungen finden [Sie unter Einstieg in die Entwicklung von Visual Studio-Erweiterungen](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Erweitern des SharePoint-Projekt Systems](../sharepoint/extending-the-sharepoint-project-system.md)
- [Erweitern des Knotens "SharePoint-Verbindungen" in Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Programmier Konzepte und Funktionen für Erweiterungen für SharePoint-Tools](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Referenz &#40;Erweiterbarkeit von SharePoint-Tools&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Debuggen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
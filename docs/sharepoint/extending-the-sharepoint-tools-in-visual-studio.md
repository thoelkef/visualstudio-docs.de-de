---
title: Erweitern der SharePoint-Tools in Visual Studio | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01a595536b85bac6948cee607af2e0897a7be1c7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890981"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Erweitern von SharePoint-Tools in Visual Studio
  SharePoint-Tools in Visual Studio erfüllt die Anforderungen von vielen verschiedenen Entwicklung. Allerdings könnten Sie feststellen, Fälle, in dem sie keine Funktionen bieten, die Sie oder andere Entwickler benötigen. In diesen Fällen können Sie die SharePoint-Tools, um die Funktionalität zu erstellen, die Sie benötigen erweitern.

## <a name="how-to-extend-the-sharepoint-tools"></a>Gewusst wie: Erweitern der SharePoint-tools
 Sie können SharePoint-Projektsystem erweitern und die **SharePoint-Verbindungen** Knoten in der **Server-Explorer** Fenster.

### <a name="extend-the-sharepoint-project-system"></a>Erweitern von SharePoint-Projektsystem
 Visual Studio enthält eine Reihe von Projektvorlagen und Elementvorlagen, die Sie verwenden können, um SharePoint-Lösungen zu erstellen. Es gibt z. B. Vorlagen für Ereignisempfänger, Listendefinitionen, Workflows und WebParts. Sie können jedoch auch eigene Typen von SharePoint-Projektelemente zum Erstellen von SharePoint-Komponenten, z. B. Felder oder benutzerdefinierte Aktionen definieren. Sie können auch die erstellen-Erweiterungen für SharePoint-Projektelementtypen, die in Visual Studio bereits installiert sind, und Sie können Extensions für SharePoint-Projekte erstellen.

 Weitere Informationen finden Sie unter [Erweitern der SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Erweitern des SharePoint-Verbindungsknotens im Server-Explorer
 In Visual Studio können Sie die **SharePoint-Verbindungen** Knoten in der **Server-Explorer** Fenster aus, um viele der Komponenten von einem oder mehreren lokalen SharePoint-Websites in einer hierarchischen Strukturansicht anzeigen. Sie können auch erweitern, die **SharePoint-Verbindungen** Knoten gibt folgende Möglichkeiten:

- Indem Sie Ihre eigenen Knoten hinzufügen. Dies ist hilfreich, wenn Sie Komponenten von SharePoint-Websites anzuzeigen, die nicht standardmäßig angezeigt werden soll.

- Durch das Erweitern von vorhandener Knoten. Beispielsweise können Sie einen neuen untergeordneten Knoten zu einem vorhandenen Knoten hinzufügen, oder Sie können hinzufügen ein Kontextmenüelements zu einem Knoten und Aufgaben ausführen, wenn ein Entwickler auf das Menüelement klickt.

  Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Anforderungen für die computer
 Um das Erweiterungen für die SharePoint-Tools zu erstellen, muss Ihre Entwicklungscomputer, auf die gleichen Anforderungen für das Erstellen von SharePoint-Lösungen in Visual Studio erfüllen.

 Wir empfehlen auch die Installation der [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Das SDK umfasst Projektvorlagen und Tools, die Sie zum Erweitern von Visual Studio verwenden können. Insbesondere enthält das SDK eine Projektvorlage, die Sie verwenden können, auf einfache Weise ein Paket von Visual Studio-Erweiterung (VSIX) zu erstellen. VSIX-Pakete sind die bevorzugte Methode zum Bereitstellen von Visual Studio-Erweiterungen in Visual Studio. Alle SharePoint-Tools-Erweiterungen müssen mit der VSIX-Pakete bereitgestellt werden. Alle exemplarischen Vorgehensweisen in dieser Dokumentation wird davon ausgegangen, dass Sie haben die [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installiert.

 Um das Visual Studio SDK installieren zu können, finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Weitere Informationen zu Visual Studio-Erweiterungen finden Sie unter [ab, die für Visual Studio-Erweiterungen entwickeln](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Siehe auch

- [Übersicht über das Programmiermodell von SharePoint-tools extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Erweitern von SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md)
- [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Programmierkonzepte und Funktionen für die SharePoint-Tools-Erweiterungen](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Verweis &#40;Erweiterbarkeit von SharePoint-Tools&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Debuggen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
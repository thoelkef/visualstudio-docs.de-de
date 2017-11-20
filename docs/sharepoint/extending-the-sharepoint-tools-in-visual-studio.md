---
title: Erweitern der SharePoint-Tools in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b78f90df8b6e46774310bd4a8cf218fbcbc7a18b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-sharepoint-tools-in-visual-studio"></a>Erweitern der SharePoint-Tools in Visual Studio
  SharePoint-Tools in Visual Studio werden die vielen Anwendungsszenarios Entwicklung erfüllen. Allerdings fest Fällen, in denen sie keine Funktionalität bieten, die Sie oder andere Entwickler benötigen. In diesen Fällen können Sie die SharePoint-Tools, um die Funktionalität zu erstellen, die Sie erweitern.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Gewusst wie: Erweitern der SharePoint-Tools  
 Sie können SharePoint-Projektsystem erweitern und die **SharePoint-Verbindungen** Knoten in der **Server-Explorer** Fenster.  
  
### <a name="extending-the-sharepoint-project-system"></a>Erweitern des SharePoint-Projektsystems  
 Visual Studio enthält eine Reihe von Projektvorlagen und Elementvorlagen, die Sie verwenden können, um SharePoint-Lösungen zu erstellen. Es gibt z. B. Vorlagen für Ereignisempfänger, Listendefinitionen, Workflows und WebParts. Sie können jedoch auch eigene Typen von SharePoint-Projektelemente zum Erstellen von SharePoint-Komponenten, z. B. Felder oder benutzerdefinierte Aktionen definieren. Sie können auch erstellen, Erweiterungen für SharePoint-Projektelementtypen, die in Visual Studio bereits installiert sind, und können Sie Erweiterungen für SharePoint-Projekte erstellen.  
  
 Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Erweitern des SharePoint-Verbindungsknotens im Server-Explorer  
 In Visual Studio können Sie die **SharePoint-Verbindungen** Knoten in der**Server-Explorer** Fenster viele Komponenten eines oder mehrere lokale SharePoint-Websites in einer hierarchischen Strukturansicht an. Sie können auch erweitern, die **SharePoint-Verbindungen** Knoten auf folgende Weise:  
  
-   Indem Sie Ihren eigenen Knoten hinzufügen. Dies ist hilfreich, wenn Sie Komponenten von SharePoint-Websites anzuzeigen, die nicht standardmäßig angezeigt werden soll.  
  
-   Durch das Erweitern von vorhandener Knoten. Beispielsweise können Sie einen neuen untergeordneten Knoten zu einem vorhandenen Knoten hinzufügen, oder Sie können hinzufügen ein Kontextmenüelements zu einem Knoten und Aufgaben ausführen, wenn ein Entwickler das Menüelement klickt.  
  
 Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Computeranforderungen Entwicklung  
 Um Erweiterungen für die SharePoint-Tools zu erstellen, muss dem Entwicklungscomputer die gleichen Anforderungen zum Erstellen von SharePoint-Lösungen in Visual Studio erfüllen. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Zudem wird empfohlen, dass Sie installieren die [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Das SDK enthält Projektvorlagen und Tools, die Sie zum Erweitern von Visual Studio verwenden können. Insbesondere enthält das SDK eine Projektvorlage, die Sie verwenden können, auf einfache Weise ein Paket von Visual Studio-Erweiterung (VSIX) zu erstellen. VSIX-Pakete sind die bevorzugte Methode zum Bereitstellen von Visual Studio-Erweiterungen in Visual Studio. Alle SharePoint-Tools-Erweiterungen müssen bereitgestellt werden, mithilfe des VSIX-Pakete. Allen exemplarischen Vorgehensweisen in dieser Dokumentation wird davon ausgegangen, dass Sie haben die [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installiert.  
  
 Um das Visual Studio SDK installieren zu können, finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Weitere Informationen zu Visual Studio-Erweiterungen finden Sie unter [starten Visual Studio-Erweiterungen entwickeln](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Programmiermodell von SharePoint-Tools-Erweiterungen](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programmierkonzepte und Features für SharePoint-Tools-Erweiterungen](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Referenz &#40; Erweiterbarkeit von SharePoint-Tools &#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debuggen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  
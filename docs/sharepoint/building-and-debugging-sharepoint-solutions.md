---
title: "Erstellen und Debuggen von SharePoint-Lösungen | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7582b0bcef8a97de14fb3b931745d6dcc21fa876
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="building-and-debugging-sharepoint-solutions"></a>Erstellen und Debuggen von SharePoint-Lösungen
  Im Allgemeinen erstellen und Debuggen von SharePoint-Lösungen ist identisch mit dem Erstellen und Debuggen von anderen Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Die vorhandenen Unterschiede werden in diesen Themen des Abschnitts erläutert.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Projektausgabe für SharePoint-Lösungen  
 Erstellen von SharePoint-Lösungen erstellt, Assemblys und eine Lösung-Paketdatei (.wsp). Die folgende Tabelle zeigt die Speicherorte dieser Dateien während eines Builds.  
  
|Element erstellen|Ausgabeordner|  
|----------------|-------------------|  
|Assembly, die Programmdatenbank (PDB) und die WSP-Dateien.|*Projektname*\bin\debug oder *Projektname*\bin\release|  
|SharePoint-Projektelementdateien.|*Projektname*\pkg\debug oder *Projektname*\pkg\release|  
|Temporäre Dateien zu erstellen.|*Projektname*\obj\debug oder *Projektname*\obj\release|  
|Intermediate Paketdateien.|*Projektname*\pkgobj\debug oder *Projektname*\pkgobj\release|  
  
## <a name="building-sharepoint-solutions"></a>Erstellen von SharePoint-Lösungen  
 Um SharePoint-Lösungen zu erstellen, muss dem Entwicklungscomputer die richtige Version von SharePoint-Server installiert haben. Andernfalls, Erstellen von SharePoint-Lösungen entspricht dem Erstellen von anderen Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von SharePoint-Lösungen](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debugging-and-testing-sharepoint-solutions"></a>Debuggen und Testen von SharePoint-Lösungen  
 Vor dem Debuggen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopiert die WSP-Paket auf dem SharePoint-Server, die Website und die Web-Funktionen aktiviert und in einigen Fällen startet das Projekt. In anderen Fällen müssen Sie möglicherweise das Projekt manuell zu öffnen. Weitere Informationen finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md) und [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debugging-and-verifying-sharepoint-solutions-by-using-alm-features"></a>Debuggen und Überprüfen von SharePoint-Lösungen mithilfe von ALM-Funktionen  
 Visual Studio ALM-Funktionen, z. B. Komponententests und IntelliTrace ermöglichen Ihnen eine präzise Aspekte erarbeiten Probleme in Ihren SharePoint-Lösungen. Die profilerstellung ermöglicht es Ihnen zu suchen, und Ermitteln von Problembereichen Leistung, in die SharePoint-Lösungen. Weitere Informationen finden Sie unter [überprüfen und Debuggen von SharePoint-Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) und [Anwendungsprofilen die Leistung von SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Sicherheit während des Buildprozesses  
 Zum Verpacken oder Bereitstellen von SharePoint-Lösungen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] benötigen die Berechtigung zum Kopieren von Dateien auf dem SharePoint-Server. Führen Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Konto muss als ein Prozess mit erhöhten Rechten, und der Benutzer einen Websitesammlungsadministrator auf dem SharePoint-Server sein. Darüber hinaus müssen Sie angeben, ob das Projekt einer sandkastenlösung oder einer farmlösung ist. Weitere Informationen finden Sie unter [Unterschiede zwischen Sandkasten- und Farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Verwenden des Befehls „Bereinigen“  
 Bei der Installation einer SharePoint-Lösung auf einem SharePoint-Server für das Debuggen, die **Bereinigen** Befehl wird die Projektmappe nicht deinstalliert. Stattdessen müssen Sie die Funktionen über die SharePoint-Konfiguration deaktivieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
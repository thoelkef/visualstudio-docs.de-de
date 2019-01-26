---
title: Erstellen und Debuggen von SharePoint-Lösungen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1cdcf71821bd0f7e9739bc194834500c2dfc6fd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871559"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Erstellen und Debuggen von SharePoint-Lösungen
  Im Allgemeinen erstellen und Debuggen von SharePoint-Lösungen ist identisch mit dem Erstellen und Debuggen von anderen Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Die vorhandenen Unterschiede werden in diesen Themen des Abschnitts erläutert.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Projektausgabe für SharePoint-Lösungen
 Erstellen von SharePoint-Lösungen erstellt, Assemblys und ein Lösungspaket (*.wsp*) Datei. Die folgende Tabelle zeigt die Speicherorte dieser Dateien während eines Builds.  
  
|Element erstellen|Ordner "Output"|  
|----------------|-------------------|  
|Assembly, die Programmdatenbank (*PDB*), und *.wsp* Dateien.|*\<ProjectName > \bin\debug* oder  *\<Projektname > \bin\release*|  
|SharePoint-Projektelementdateien.|*\<Projektname > \pkg\debug* oder  *\<Projektname > \pkg\release*|  
|Temporäre Dateien zu erstellen.|*\<Projektname > \obj\debug* oder  *\<Projektname > \obj\release*|  
|Temporäre Dateien des Pakets.|*\<Projektname > \pkgobj\debug* oder  *\<Projektname > \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>Erstellen von SharePoint-Lösungen
 Um SharePoint-Lösungen zu erstellen, muss dem Entwicklungscomputer die richtige Version von SharePoint-Server installiert haben. Andernfalls erstellen die SharePoint-Lösungen ist identisch mit Erstellen anderer Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von SharePoint-Lösungen](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Debuggen und Testen von SharePoint-Lösungen
 Vor dem Debuggen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Kopien der *.wsp* -Paket mit dem SharePoint-Server die Website- und Web-Funktionen aktiviert und in einigen Fällen startet das Projekt. In anderen Fällen müssen Sie möglicherweise das Projekt manuell zu öffnen. Weitere Informationen finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md) und [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Debuggen Sie und überprüfen Sie SharePoint-Lösungen mithilfe von Azure DevOps-Services-Funktionen
 Azure DevOps-Services-Funktionen wie Komponententests und IntelliTrace können Sie genauere Bestimmung von Problemen in Ihren SharePoint-Lösungen. Die profilerstellung ermöglicht es Ihnen zu suchen, und Ermitteln von Problembereichen Leistung, in die SharePoint-Lösungen. Weitere Informationen finden Sie unter [überprüfen und Debuggen von SharePoint-Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) und [Profilerstellung der Leistung von SharePoint-Anwendungen](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Sicherheit während des Buildprozesses
 Verpacken oder Bereitstellen von SharePoint-Lösungen, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] müssen über die Berechtigung zum Kopieren von Dateien auf dem SharePoint-Server. Sie müssen ausführen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Konto muss als einen erhöhten Prozess ausführen, und der Benutzer einen Websitesammlungsadministrator auf dem SharePoint-Server sein. Darüber hinaus müssen Sie angeben, ob das Projekt einer sandkastenlösung oder farmlösung ist. Weitere Informationen finden Sie unter [Unterschiede zwischen Sandkasten- und Farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Mithilfe der Befehls "bereinigen"  
 Bei der Installation auf einem SharePoint-Server für das Debuggen einer SharePoint-Lösung die **Bereinigen** Befehl wird die Lösung nicht deinstalliert. Stattdessen müssen Sie die Funktionen über die SharePoint-Konfiguration deaktivieren.  
  
## <a name="see-also"></a>Siehe auch
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Durchsuchen von SharePoint-Verbindungen mit Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  

---
title: Entwickeln und Debuggen von SharePoint-Lösungen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: e4b34df23c8cb612d72fed108a6c0aecbf57875c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016369"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Erstellen und Debuggen von SharePoint-Lösungen
  Im Allgemeinen ist das entwickeln und Debuggen von SharePoint-Lösungen das gleiche wie das entwickeln und Debuggen anderer Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Die vorhandenen Unterschiede werden in diesen Themen des Abschnitts erläutert.

## <a name="project-output-for-sharepoint-solutions"></a>Projekt Ausgabe für SharePoint-Lösungen
 Beim Erstellen von SharePoint-Lösungen werden Assemblys und eine Projektmappenpaketdatei (*wsp*) erstellt In der folgenden Tabelle sind die Speicherorte dieser Dateien während eines Builds aufgeführt.

|Buildelement|Ausgabeordner|
|----------------|-------------------|
|Assembly, Programmdatenbank (*. pdb*) und *wsp* -Dateien.|* \<ProjectName> \bin\debug* oder * \<ProjectName> \bin\release*|
|SharePoint-Projekt Element Dateien.|* \<ProjectName> \pkg\debug* oder * \<ProjectName> \pkg\release*|
|Erstellen von zwischen Dateien.|* \<ProjectName> \obj\debug* oder * \<ProjectName> \obj\release*|
|Paket zwischen Dateien.|* \<ProjectName> \pkgobj\debug* oder * \<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Erstellen von SharePoint-Lösungen
 Zum Erstellen von SharePoint-Lösungen muss auf dem Entwicklungs Computer die richtige Version von SharePoint Server installiert sein. Andernfalls ist das Entwickeln von SharePoint-Lösungen identisch mit dem Aufbau anderer Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von SharePoint-Lösungen](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Debuggen und Testen von SharePoint-Lösungen
 Vor dem Debuggen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopiert das *wsp* -Paket auf den SharePoint-Server, aktiviert die Website-und webbezogenen Features und startet in einigen Fällen das Projekt. In anderen Fällen müssen Sie das Projekt möglicherweise manuell öffnen. Weitere Informationen finden Sie unter Problembehandlung bei [SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md) und [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Debuggen und Überprüfen von SharePoint-Lösungen mithilfe Azure DevOps Services Features
 Azure DevOps Services Features, wie z. b. Komponententests und IntelliTrace, ermöglichen es Ihnen, Probleme in Ihren SharePoint-Lösungen genauer zu lokalisieren. Die Profilerstellung ermöglicht es Ihnen, Leistungsprobleme in Ihren SharePoint-Lösungen zu finden und zu identifizieren. Weitere Informationen finden Sie unter über [prüfen und Debuggen von SharePoint-Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) und [Profilerstellung für die Leistung von SharePoint-Anwendungen](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Sicherheit während des Buildprozesses
 Zum Verpacken oder Bereitstellen von SharePoint-Lösungen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] muss über die Berechtigung zum Kopieren von Dateien auf den SharePoint-Server verfügen. Sie müssen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] als erweiterter Prozess ausgeführt werden, und Ihr Benutzerkonto muss auf dem SharePoint-Server ein Website Sammlungs Administrator sein. Außerdem müssen Sie angeben, ob es sich bei dem Projekt um eine Sandkasten Lösung oder eine Farm Lösung handelt. Weitere Informationen finden Sie [unter Unterschiede zwischen Sandkasten-und Farm Lösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Verwenden des Clean-Befehls
 Wenn eine SharePoint-Lösung zum Debuggen auf einem SharePoint-Server installiert ist, wird die Projekt Mappe mit dem Befehl **Clean** nicht deinstalliert. Stattdessen müssen Sie die Features über die SharePoint-Konfiguration deaktivieren.

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Durchsuchen von SharePoint-Verbindungen mit Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

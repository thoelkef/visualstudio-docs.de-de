---
title: "Erstellen und Debuggen von SharePoint-L&#246;sungen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Erstellen und Debuggen"
  - "SharePoint-Entwicklung in Visual Studio, Debuggen"
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Erstellen und Debuggen von SharePoint-L&#246;sungen
  Grundsätzlich funktioniert das Erstellen und Debuggen von SharePoint\-Lösungen genauso wie das Erstellen und Debuggen anderer Projekttypen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  In den Themen dieses Abschnitts werden die jeweiligen Unterschiede erläutert.  
  
## Projektausgabe für SharePoint\-Lösungen  
 Beim Erstellen von SharePoint\-Lösungen werden Assemblys und eine Lösungspaketdatei \(WSP\-Datei\) erstellt.  Die folgende Tabelle enthält die Speicherorte dieser Dateien während des Buildvorgangs:  
  
|Buildelement|Ausgabeordner|  
|------------------|-------------------|  
|Assembly, Programmdatenbank \(PDB\) und WSP\-Dateien|*ProjectName*\\ bin\\Debug oder *ProjectName*\\bin\\release|  
|SharePoint\-Projektelementdateien|*ProjectName*\\pkg\\debug oder *ProjectName*\\pkg\\release|  
|Build\-Zwischendateien|*ProjectName*\\obj\\debug oder *ProjectName*\\obj\\release|  
|Paket\-Zwischendateien|*ProjectName*\\pkgobj\\debug oder *ProjectName*\\pkgobj\\release|  
  
## Erstellen von SharePoint\-Lösungen  
 Zum Erstellen von SharePoint\-Lösungen muss auf dem Entwicklungscomputer die korrekte SharePoint Server\-Version installiert sein.  Ansonsten werden SharePoint\-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf die gleiche Weise erstellt wie andere Projekttypen.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von SharePoint-Lösungen](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## Debuggen und Testen von SharePoint\-Lösungen  
 Vor dem Debugging wird das WSP\-Paket von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf den SharePoint\-Server kopiert, die Website\- und Internetfunktionen werden aktiviert, und das Projekt wird ggf. gestartet.  In anderen Fällen müssen Sie möglicherweise das Projekt manuell öffnen.  Weitere Informationen finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md) und [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).  
  
## SharePoint\-Lösungen mit ALM\-Funktionen debuggen und Überprüfung  
 Visual Studio ALM\-Funktionen wie IntelliTrace und Komponententests können Sie genauer zu den in den Genauigkeitsproblemen SharePoint\-Lösungen.  Profilerstellung, können Sie in den Leistungsproblemkreise SharePoint\-Lösungen zu suchen und zu ermitteln.  Weitere Informationen finden Sie unter [Überprüfen und Debuggen von SharePoint-Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) und [Profilerstellung für die Leistung von SharePoint-Anwendungen](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## Sicherheit beim Buildprozess  
 Damit SharePoint\-Lösungen gepackt und bereitgestellt werden können, muss [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] über die Berechtigung zum Kopieren von Dateien auf den SharePoint\-Server verfügen.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] muss als Prozess mit erhöhten Rechten ausgeführt werden, und bei Ihrem Benutzerkonto muss es sich um einen Websitesammlungsadministrator auf dem SharePoint\-Server handeln.  Darüber hinaus muss angegeben werden, ob es sich bei dem Projekt um eine Sandkastenlösung oder um eine Farmlösung handelt.  Weitere Informationen finden Sie unter [Unterschiede zwischen Sandkasten- und Farmlösungen](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Verwenden des Befehls "Bereinigen"  
 Wenn eine SharePoint\-Lösung zum Debuggen auf einem SharePoint\-Server installiert ist, wird die Lösung mit dem Befehl **Bereinigen** nicht deinstalliert.  Die Funktionen müssen stattdessen mithilfe der SharePoint\-Konfiguration deaktiviert werden.  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
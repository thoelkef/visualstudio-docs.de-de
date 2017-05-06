---
title: "Gewusst wie: Festlegen von SharePoint-Bereitstellungsbefehlen"
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
  - "SharePoint-Entwicklung in Visual Studio, Bereitstellen"
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Gewusst wie: Festlegen von SharePoint-Bereitstellungsbefehlen
  Sie können den Bereitstellungsvorgang anpassen, indem Sie Befehle vor der Bereitstellung und nach der Bereitstellung festlegen.  Diese Befehle werden vor und nach anderen Bereitstellungsaktionen ausgeführt, wenn Sie SharePoint\-Lösungen für Visual Studio debuggen.  
  
### So fügen Sie einen Befehl vor der Bereitstellung hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt** und die Option für *ProjectName*\-**Eigenschaften** aus.  
  
2.  Wählen Sie die Registerkarte **SharePoint** aus.  
  
3.  Im Textfeld geben Sie **Befehlszeile vor der Bereitstellung** MS\-DOS\- oder MSBuild\-Befehle ein, um diesen Schritt anzupassen.  
  
     Um beispielsweise den Verzeichnisinhalt aufzuführen, bevor die Bereitstellung abgeschlossen wird, geben Sie **dir** ein.  
  
### So fügen Sie einen Befehl nach der Bereitstellung hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt** und die Option für *ProjectName*\-**Eigenschaften** aus.  
  
2.  Wählen Sie die Registerkarte **SharePoint** aus.  
  
3.  Im Textfeld geben Sie **Befehlszeile nach der Bereitstellung** MS\-DOS\- oder MSBuild\-Befehle ein, um diesen Schritt anzupassen.  
  
     Um beispielsweise den Verzeichnisinhalt aufzuführen, nachdem die Bereitstellung abgeschlossen ist, geben Sie **dir** ein.  Um eine MSBuild\-Variable verwenden die Assembly aus dem Buildverzeichnis zu kopieren, geben Sie **copy $\(TargetPath\) c:\\DeploymentDirectory** ein.  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
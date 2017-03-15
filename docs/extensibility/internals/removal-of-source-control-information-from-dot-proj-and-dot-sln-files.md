---
title: "Entfernen von Informationen aus. Proj und. Sln-Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins, sln- und proj-Dateien"
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Entfernen von Informationen aus. Proj und. Sln-Dateien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In Version 1.2 des Quellcodeverwaltungs\-Plug\-In APIs werden die SCC\-Informationen in einer MSSCCPRJ.SCC\-Datei gespeichert.  Der Vorteil der MSSCCPRJ.SCC\-Datei ist, dass die SCC\-Informationen nicht der Quellcodeverwaltung unterliegen, lauten wie es in .proj\- und .sln\-Dateien ist.  
  
## Änderungen der Versions\-1.2  
 In den steckverbindungen Quellcodeverwaltung auf Grundlage der Version 1.1 des Quellcodeverwaltungs\-Plug\-In APIs sind, werden Informationen über die Quellcodeverwaltung in den Dateien des Projekts \(.proj\) und die Projektmappe \(SLN\) gespeichert.  Der Speicherort der Datenbank wird durch das AuxPath Informationen zur Quellcodeverwaltung und der bestimmte Position in der Datenbank wird durch ProjName angegeben.  Dieses Verhalten kann Probleme nach Verzweigung, fork oder Kopiervorgängen verursachen, da das ProjName i. d. R. nach allen Vorgängen ungültig wäre.  
  
 In der Version 1.1 des verwendeten APIs Quellcodeverwaltungs\-Plug\-In die IDE ~SAK Dateien, um zu erkennen, wenn ein Plug\-In die MSSCCPRJ.SCC\-Methode zum Speichern von Informationen zur Quellcodeverwaltung unterstützt.  Die Version 1.2 des Quellcodeverwaltungs\-Plug\-In API erstellt eine neue Funktion zum Erkennen der Unterstützung für MSSCCPRJ.SCC\-Datei bereit, ohne eine ~SAK Datei zu verwenden.  Weitere Informationen finden Sie unter [Beseitigung von ~ SAK\-Dateien](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## Siehe auch  
 [Was ist neu in Source Control\-Plug\-in API\-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
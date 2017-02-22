---
title: "Angeben des Pfads zu den Profilerstellungstools f&#252;r die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Angeben des Pfads zu den Profilerstellungstools f&#252;r die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Pfad der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools wird der PATH\-Umgebungsvariablen nicht hinzugefügt.  Auf 32\-Bit\-Computern befinden sich die Tools in einem einzigen Verzeichnis.  Es gibt 32\-Bit und 64\-Bit\-Versionen der Profilerstellungstools auf 64\-Bit\-Computern.  
  
## 32\-Bit\-Computer  
 Auf 32\-Bit\-Computern ist das Standardverzeichnis für Profilerstellungstools *Laufwerk*\\Programme\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools.  
  
## 64\-Bit\-Computer  
 Auf 64\-Bit\-Computern legen Sie den Pfad entsprechend der Zielplattform der profilierten Anwendung fest.  
  
-   Bei 32\-Bit\-Anwendungen lautet das Standardverzeichnis für Profilerstellungstools:  
  
     *Laufwerk*\\Programme \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools  
  
-   Bei 64\-Bit\-Anwendungen lautet das Standardverzeichnis für Profilerstellungstools:  
  
     *Laufwerk*\\Programme \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools\\x64
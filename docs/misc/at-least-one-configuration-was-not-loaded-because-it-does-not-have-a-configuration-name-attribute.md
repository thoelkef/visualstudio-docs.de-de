---
title: "At least one configuration was not loaded because it does not have a configuration name attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_nameless_config"
ms.assetid: 711f7253-308b-44e0-b8bc-ca5c16536a2c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one configuration was not loaded because it does not have a configuration name attribute
Alle `<Config>`\-Abschnitte in einer CSPROJ\-Datei bzw. einer VBPROJ\-Datei müssen ein **Name**\-Attribut enthalten, das einen eindeutigen Namen für diese Konfiguration definiert.  Diese Diagnose gibt an, dass das **Name**\-Attribut fehlt.  Wenn das **Name**\-Attribut in einer Konfiguration fehlt, wird diese Konfiguration nicht in das Projekt geladen.  
  
 Dieser Fehler wird meistens durch das manuelle Bearbeiten der Projektdatei verursacht.  
  
 **So beheben Sie diesen Fehler**  
  
-   Fügen Sie direkt nach der `<Config>` \-Zeile einen Konfigurationsnamen in die Projektdatei ein.  
  
    ```  
    Name = "someconfigname"  
    ```  
  
     Ein typischer Konfigurationsname ist `Debug` oder `Release`.  
  
## Siehe auch  
 [Projektdateien](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/de-de/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)
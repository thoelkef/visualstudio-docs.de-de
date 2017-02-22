---
title: "Befehl Einstellungen importieren und exportieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Tools.ImportandExportSettings"
helpviewer_keywords: 
  - "Tools.ImportandExportSettings"
  - "Befehl Einstellungen importieren und exportieren"
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl Einstellungen importieren und exportieren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Importiert oder exportiert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Einstellungen bzw. setzt diese zurück.  
  
## Syntax  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## Schalter  
 \/export:`filename`  
 Optional.  Exportiert die aktuellen Einstellungen in die angegebene Datei.  
  
 \/import:`filename`  
 Optional.  Importiert die Einstellungen in die angegebene Datei.  
  
 \/reset  
 Optional.  Setzt die aktuellen Einstellungen zurück.  
  
## Hinweise  
 Wenn Sie diesen Befehl ohne Schalter ausführen, wird der **Assistent zum Importieren und Exportieren von Einstellungen** geöffnet.  Weitere Informationen finden Sie unter [How to: Share Settings Between Computers or Visual Studio Versions](http://msdn.microsoft.com/de-de/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## Beispiel  
 Mit dem folgenden Befehl werden die aktuellen Einstellungen in die Datei `MyFile.vssettings` exportiert.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## Siehe auch  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)
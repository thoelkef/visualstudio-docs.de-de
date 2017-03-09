---
title: "/Command (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/command (Devenv-Schalter)"
  - "Devenv, /command-Schalter"
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Command (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet die integrierte Entwicklungsumgebung \(IDE\) von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und führt dann den angegebenen Befehl aus.  
  
## Syntax  
  
```  
devenv /command CommandName  
```  
  
## Argumente  
 `CommandName`  
 Erforderlich.  Der vollständige Name eines [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Befehls oder dessen Aliasname in doppelten Anführungszeichen.  Weitere Informationen zur Syntax von Befehlen und Alias finden Sie unter [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md).  
  
## Hinweise  
 Nachdem der Startvorgang abgeschlossen wurde, wird der genannte Befehl in der IDE ausgeführt.  Bei Verwendung dieses Schalters wird in der IDE beim Start nicht die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Startseite angezeigt.  
  
 Wenn ein Befehl mittels eines Add\-Ins verfügbar gemacht wird, können Sie das Add\-In mithilfe dieses Schalters von der Befehlszeile aus starten.  Weitere Informationen finden Sie unter [Gewusst wie: Steuern von Add\-Ins mit dem Add\-In\-Manager](../Topic/How%20to:%20Control%20Add-Ins%20By%20Using%20the%20Add-In%20Manager.md).  
  
## Beispiel  
 In diesem Beispiel wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestartet und automatisch das Makro "Open Favorite Files" ausgeführt.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)
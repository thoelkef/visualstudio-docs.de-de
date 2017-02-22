---
title: "Fehler: SSDEBUGPS wurde von SQL nicht gefunden | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_cant_find_ssdebugps"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "SQL"
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: SSDEBUGPS wurde von SQL nicht gefunden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

SSDEBUGPS.dll ist die Hostkomponente von SQL Server\-Debuggen.  
  
 Dieser Fehler tritt beim Versuch auf, das Debuggen zu starten, und zeigt an, dass die angegebene Datei nicht auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]\-Computer ist.  Mögliche Ursachen sind: Entweder wurde Remotedebuggen\-Setup nie ausgeführt, oder diese Datei wurde gelöscht.  
  
 Es gibt zwei Möglichkeiten, diesen Fehler zu beheben: Entweder führen Sie Remotedebuggen\-Setup erneut aus, oder Sie kopieren die Datei auf den [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]\-Computer.  
  
 Um Remotedebuggen\-Setup erneut auszuführen, befolgen Sie die Anweisungen in [Remotedebugging](../debugger/remote-debugging.md).  
  
 Wenn Sie eine Kopie von ssdebugps.dll finden, können Sie sie auf den [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]\-Computer kopieren.  Wenn die Datei vorhanden ist, finden Sie sie im Verzeichnis \\Programme\\Gemeinsame Dateien\\Microsoft Shared\\SQL\-Debuggen.  Sie finden sie möglicherweise auf einem anderen [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]\-Computer oder auf einem Computer, auf dem [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] installiert ist.  
  
### So kopieren Sie SSDEBUGPS.dll auf den SQL Server 2005\-Computer  
  
1.  Kopieren Sie die Datei in das Verzeichnis mit dem gleichen Namen und Pfad auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]\-Computer.  
  
2.  Registrieren Sie sie, indem Sie eine **Eingabeaufforderung** öffnen und den folgenden Befehl ausführen:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```
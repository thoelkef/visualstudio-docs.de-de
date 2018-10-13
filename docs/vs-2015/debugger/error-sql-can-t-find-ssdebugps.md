---
title: 'Fehler: SQL kann&#39;finden SSDEBUGPS wurde von | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f775bd99c019a119d1bcd5193df0efd7ceadd096
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180166"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Fehler: SQL kann&#39;finden SSDEBUGPS wurde von
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll ist die Hostkomponente von SQL Server-Debuggen.  
  
 Dieser Fehler tritt beim Versuch auf, das Debuggen zu starten, und zeigt an, dass die angegebene Datei nicht auf dem [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]-Computer ist. Mögliche Ursachen sind: Entweder wurde Remotedebuggen-Setup nie ausgeführt, oder diese Datei wurde gelöscht.  
  
 Es gibt zwei Möglichkeiten zum Beheben dieses Fehlers: indem Sie Remotedebuggen-Setup ausführen und durch Kopieren der Datei auf den [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] Computer.  
  
 Um Remotedebuggen-Setup erneut auszuführen, befolgen Sie die Anweisungen unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
 Wenn Sie eine Kopie von ssdebugps.dll finden können, können Sie kopieren sie auf die [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] Computer. Wenn die Datei vorhanden ist, finden Sie sie im Verzeichnis \Programme\Gemeinsame Dateien\Microsoft Shared\SQL-Debuggen. Sie finden es vielleicht auf einem anderen [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] -Computer oder auf einem Computer mit [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] installiert.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>So kopieren Sie SSDEBUGPS.dll auf den SQL Server 2005-Computer  
  
1.  Kopieren Sie die Datei in das Verzeichnis mit dem gleichen Namen und Pfad für die [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] Computer.  
  
2.  Registrieren Sie ihn durch Öffnen einer **Eingabeaufforderung**, und den folgenden Befehl ausführen:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```




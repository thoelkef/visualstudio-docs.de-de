---
title: 'Fehler: SQL kann&#39;finden SSDEBUGPS wurde von | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33e6efb699d12cc58555cacede6a20c5b0091d0d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959617"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Fehler: SQL kann&#39;finden SSDEBUGPS wurde von
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll ist die Hostkomponente von SQL Server-Debuggen.  
  
 Dieser Fehler tritt beim Versuch auf, das Debuggen zu starten, und zeigt an, dass die angegebene Datei nicht auf dem [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]-Computer ist. Mögliche Ursachen sind: Entweder wurde Remotedebuggen-Setup nie ausgeführt, oder diese Datei wurde gelöscht.  
  
 Es gibt zwei Möglichkeiten, diesen Fehler zu beheben: Entweder führen Sie Remotedebuggen-Setup erneut aus, oder Sie kopieren die Datei auf den [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]-Computer.  
  
 Um Remotedebuggen-Setup erneut auszuführen, befolgen Sie die Anweisungen unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
 Wenn Sie eine Kopie von „ssdebugps.dll“ finden, können Sie sie auf den [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]-Computer kopieren. Wenn die Datei vorhanden ist, finden Sie sie im Verzeichnis \Programme\Gemeinsame Dateien\Microsoft Shared\SQL-Debuggen. Sie finden es vielleicht auf einem anderen [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] -Computer oder auf einem Computer mit [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] installiert.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>So kopieren Sie SSDEBUGPS.dll auf den SQL Server 2005-Computer  
  
1.  Kopieren Sie die Datei in das Verzeichnis mit dem gleichen Namen und Pfad auf dem [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]-Computer.  
  
2.  Registrieren Sie sie, indem Sie eine **Eingabeaufforderung** öffnen und den folgenden Befehl ausführen:  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```

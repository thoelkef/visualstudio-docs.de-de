---
title: "Fehler: SQL können &#39; t Find SSDEBUGPS | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 69a82222fe1a4a2cd643f9f84127c3674f8078fd
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Fehler: SQL können &#39; t Find SSDEBUGPS

SSDEBUGPS.dll ist die Hostkomponente von SQL Server-Debuggen.

Dieser Fehler tritt beim Versuch auf, das Debuggen zu starten, und zeigt an, dass die angegebene Datei nicht auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer ist. Mögliche Ursachen sind: Entweder wurde Remotedebuggen-Setup nie ausgeführt, oder diese Datei wurde gelöscht.

Es gibt zwei Möglichkeiten zum Beheben dieses Fehlers: indem Sie Remotedebuggen-Setup erneut ausführen und kopieren die Datei auf die [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] Computer.

Zum Remotedebuggen-Setup erneut ausführen, befolgen Sie die Anweisungen unter [Remotedebuggen](../debugger/remote-debugging.md).

Wenn Sie eine Kopie von ssdebugps.dll finden können, können Sie kopieren sie auf der [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] Computer. Wenn die Datei vorhanden ist, finden Sie sie im Verzeichnis \Programme\Gemeinsame Dateien\Microsoft Shared\SQL-Debuggen. Sie finden es vielleicht auf einem anderen [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] Computer oder auf einem Computer mit Visual Studio 2005 installiert.

So kopieren Sie SSDEBUGPS.dll auf dem SQL Server 2005-Computer:

1. Kopieren Sie die Datei in das Verzeichnis mit dem gleichen Namen und Pfad auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] Computer.

2. Registrieren Sie ihn durch Öffnen einer **Eingabeaufforderung**, und den folgenden Befehl ausführen:

    ```
    regsrv32 ssdebugps.dll
    ```
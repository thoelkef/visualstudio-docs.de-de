---
title: 'Fehler: SQL kann&#39;t suchen SSDEBUGPS | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f263d76667eb197d85a99ba06a45fc08e2f4d0d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472837"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Fehler: SQL kann&#39;t suchen SSDEBUGPS

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
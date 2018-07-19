---
title: 'Fehler: SQL kann&#39;finden SSDEBUGPS wurde von | Microsoft-Dokumentation'
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
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058255"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Fehler: SQL kann&#39;finden SSDEBUGPS wurde von

SSDEBUGPS.dll ist die Hostkomponente von SQL Server-Debuggen.

Dieser Fehler tritt beim Versuch auf, das Debuggen zu starten, und zeigt an, dass die angegebene Datei nicht auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer ist. Mögliche Ursachen sind: Entweder wurde Remotedebuggen-Setup nie ausgeführt, oder diese Datei wurde gelöscht.

Es gibt zwei Möglichkeiten zum Beheben dieses Fehlers: indem Sie Remotedebuggen-Setup ausführen und durch Kopieren der Datei auf den [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] Computer.

Um Remotedebuggen-Setup erneut auszuführen, befolgen Sie die Anweisungen unter [Remotedebuggen](../debugger/remote-debugging.md).

Wenn Sie eine Kopie von ssdebugps.dll finden können, können Sie kopieren sie auf die [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] Computer. Wenn die Datei vorhanden ist, finden Sie sie im Verzeichnis \Programme\Gemeinsame Dateien\Microsoft Shared\SQL-Debuggen. Sie finden es vielleicht auf einem anderen [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] -Computer oder auf einem Computer mit Visual Studio 2005 installiert.

So kopieren Sie SSDEBUGPS.dll auf den SQL Server 2005-Computer:

1. Kopieren Sie die Datei in das Verzeichnis mit dem gleichen Namen und Pfad für die [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] Computer.

2. Registrieren Sie ihn durch Öffnen einer **Eingabeaufforderung**, und den folgenden Befehl ausführen:

    ```cmd
    regsrv32 ssdebugps.dll
    ```

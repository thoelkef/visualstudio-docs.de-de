---
title: 'Fehler: SQL kann&#39;finden SSDEBUGPS wurde von | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
ms.openlocfilehash: 038b448c0ecd0b19afd7671a381eb68c9ba8cbbe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854112"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Fehler: SQL kann&#39;finden SSDEBUGPS wurde von

SSDEBUGPS.dll ist die Hostkomponente von SQL Server-Debuggen.

Dieser Fehler tritt beim Versuch auf, das Debuggen zu starten, und zeigt an, dass die angegebene Datei nicht auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer ist. Mögliche Ursachen sind: Entweder wurde Remotedebuggen-Setup nie ausgeführt, oder diese Datei wurde gelöscht.

Es gibt zwei Möglichkeiten, diesen Fehler zu beheben: Entweder führen Sie Remotedebuggen-Setup erneut aus, oder Sie kopieren die Datei auf den [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer.

Um Remotedebuggen-Setup erneut auszuführen, befolgen Sie die Anweisungen unter [Remotedebuggen](../debugger/remote-debugging.md).

Wenn Sie eine Kopie von „ssdebugps.dll“ finden, können Sie sie auf den [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer kopieren. Wenn die Datei vorhanden ist, finden Sie sie im Verzeichnis \Programme\Gemeinsame Dateien\Microsoft Shared\SQL-Debuggen. Sie finden es vielleicht auf einem anderen [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] -Computer oder auf einem Computer mit Visual Studio 2005 installiert.

So kopieren Sie „SSDEBUGPS.dll“ auf den SQL Server 2005-Computer:

1. Kopieren Sie die Datei in das Verzeichnis mit dem gleichen Namen und Pfad auf dem [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]-Computer.

2. Registrieren Sie sie, indem Sie eine **Eingabeaufforderung** öffnen und den folgenden Befehl ausführen:

    ```cmd
    regsrv32 ssdebugps.dll
    ```

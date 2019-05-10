---
title: 'Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c4ab45feeae409a1951e1a57e964eaaa5963896
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902583"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen
Diese Warnmeldung wird bei Verwendung des Quellservers angezeigt. Diese Meldung besagt, dass der Befehl, den der Debugger zum Abrufen von Quellcode ausführen muss, nicht in der Liste der vertrauenswürdigen Befehle für Quellserver in der Datei "srcsvr.ini" aufgeführt ist. Wenn dies ein gültiger Befehl ist, können Sie ihn der Datei "srcsvr.ini" hinzufügen. Andernfalls sollten Sie ihn nicht ausführen. Weitere Informationen finden Sie unter [Angeben von Symbol (.pdb)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Meldungstext
 **Der Debugger muss den folgenden nicht vertrauenswürdigen Befehl ausführen, um Quellcode vom Quellserver abzurufen.**

 **Wenn die Debugsymboldatei (\*.pdb) nicht aus einer bekannten und vertrauenswürdigen Quelle stammt, ist dieser Befehl möglicherweise ungültig oder kann nicht sicher ausgeführt werden.**

 **Möchten Sie diesen Befehl ausführen?**

## <a name="uielement-list"></a>UIElement-Liste
 Text aus der PDB-Datei im Befehl ausführen.

 Führen Sie können den Befehl zum Ausführen.

 Keine Ausführung Beenden der Ausführung des Befehls und das Herunterladen der Datei vom Quellserver.

## <a name="see-also"></a>Siehe auch
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Quellserver](/windows/desktop/Debug/source-server-and-source-indexing)
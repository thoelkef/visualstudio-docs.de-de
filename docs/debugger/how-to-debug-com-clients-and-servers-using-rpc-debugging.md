---
title: Debuggen von com-Clients und-Servern mit RPC-Debugging Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cca09e917cddffd0d1d844db14ae8a4ca4f0088
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211076"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Vorgehensweise: RPC-Debuggen von COM-Clients und -Servern
Sie können RPC-Debuggen (Remote Procedure Call, Remoteprozeduraufruf) verwenden, um COM-Client-/Server-Anwendungen zu debuggen. Vor der Verwendung muss RPC-Debuggen allerdings aktiviert werden. Bei aktiviertem RPC-Debuggen wird der Debugger an den Server angefügt, wenn Sie vom Client in den Serveraufruf springen. Der Code kann nun debuggt werden. Wenn der Debugger angefügt wurde, können alle Debuggerfunktionen sowohl für Client- als auch für Serverprozesse verwendet werden.

### <a name="to-enable-rpc-debugging"></a>So aktivieren Sie RPC-Debuggen

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Klicken Sie im Dialogfeld **Optionen** auf den Ordner **Debuggen**.

3. Klicken Sie auf die Seite **Native** (Nativ).

4. Aktivieren Sie das Kontrollkästchen **RPC-Debuggen**.

    > [!NOTE]
    > Sie müssen Administrator- oder Hauptbenutzerrechte besitzen, um Remoteprozeduraufrufe debuggen zu können.

    > [!NOTE]
    > RPC-Stepping auf einem Remoteserver, auf dem Microsoft Windows Vista ausgeführt wird, funktioniert nur, wenn ein systemeigener Debugger an den Remoteserver angehängt wird. Andernfalls schlägt der RPC-Aufruf ohne eine Fehlermeldung fehl. Sonst wird der RPC-Aufruf abgeschlossen, aber der Einzelschritt beim RPC-Aufruf funktioniert nicht.

## <a name="see-also"></a>Siehe auch
- [Debuggen von COM-Servern und -Containern](../debugger/com-server-and-container-debugging.md)
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
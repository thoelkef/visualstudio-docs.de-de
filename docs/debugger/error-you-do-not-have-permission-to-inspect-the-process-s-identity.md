---
title: 'Fehler: Sie verfügen nicht über die Berechtigung, die Identität&#39;des Prozesses zu überprüfen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cad229f80676c3d1f7a7d23ad7a29729c834929b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736220"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Fehler: Sie verfügen nicht über die Berechtigung zum Überprüfen&#39;der Identität des Prozesses.
Sie haben keine Berechtigung, die Prozessidentität zu überprüfen. Dies liegt möglicherweise an der Konfiguration des Systems.

 Der Debugger konnte die Prozessidentität nicht überprüfen, was für das Debuggen aber erforderlich ist. Die wahrscheinlichste Ursache ist die Deaktivierung der Terminaldienste. Der Dienst Terminaldienste ist standardmäßig aktiviert. Führen Sie diese Schritte aus, um den Dienst wieder zu aktivieren.

### <a name="to-enable-terminal-services"></a>So aktivieren Sie die Terminaldienste

1. Klicken Sie auf das Menü **Start**, und wählen Sie anschließend **Systemsteuerung** aus.

2. Wählen Sie in der Systemsteuerung ggf. die Option **Zur klassischen Ansicht wechseln**, und doppelklicken Sie auf **Verwaltung**.

3. Doppelklicken Sie im Fenster **Verwaltung** auf **Computerverwaltung**.

4. Erweitern Sie im Fenster „Computerverwaltung“ den Knoten **Dienste und Anwendungen**.

5. Klicken Sie unter **Dienste und Anwendungen** auf **Dienste**.

     Eine Liste von Diensten wird im rechten Bereich angezeigt.

6. Klicken Sie in der Liste **Dienste** mit der rechten Maustaste auf **Terminaldienste**, und wählen Sie dann **Eigenschaften** aus.

7. Wechseln Sie im Fenster **Eigenschaften von Terminal Dienste** zur Register **Karte allgemein** , und legen Sie **Starttyp** auf **manuell**fest.

8. Klicken Sie auf **OK**.

9. Starten Sie den Computer neu.

     Durch diesen Vorgang wird Remotedesktop nicht automatisch aktiviert. Wenn Sie Remotedesktop auf dem Computer aktivieren möchten, führen Sie zusätzlich die folgenden Schritte aus.

### <a name="to-enable-remote-desktop"></a>So aktivieren Sie Remotedesktop

1. Klicken Sie auf **Start**, und klicken Sie dann mit der rechten Maustaste auf **Arbeitsplatz**.

2. Klicken Sie auf **Eigenschaften**.

     Das Fenster **Systemeigenschaften** wird angezeigt.

3. Klicken Sie auf **Remote**.

4. Wählen Sie unter **Remotedesktop** die Option **Benutzer dürfen eine Remotedesktopverbindung herstellen** aus.

5. Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
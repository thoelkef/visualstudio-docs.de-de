---
title: 'Fehler: Der Visual Studio-Remotedebugdienst auf dem Zielcomputer kann keine Rückverbindung mit diesem Computer herstellen'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
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
ms.openlocfilehash: 695c4c9e84ce9eb851a551dc9821bff00123a35c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737407"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Fehler: Der Visual Studio-Remotedebugdienst auf dem Zielcomputer kann keine Rückverbindung mit diesem Computer herstellen
Dieser Fehler bedeutet, dass der Remotedebugdienst unter einem Benutzerkonto ausgeführt wird, das sich nicht authentifizieren kann, wenn es versucht, eine Verbindung mit dem Computer herzustellen, von dem aus Sie Debuggen. Dieser Fehler kann auftreten, wenn das Remote Debuggen mit der Legacy-debuggingengine und der Remote Debugger als Dienst ausgeführt wird.

 Die folgende Tabelle zeigt, welche Konten auf den Computer zugreifen können:

|||||
|-|-|-|-|
||LocalSystem-Konto|Domänenkonto|Lokale Konten mit identischem Benutzernamen und -kennwort auf beiden Computern|
|Beide Computer in derselben Domäne|Ja|Ja|Ja|
|Beide Computer in Domänen mit bidirektionaler Vertrauenswürdigkeit|Nein|Nein|Ja|
|Einer oder beide Computer in einer Arbeitsgruppe|Nein|Nein|Ja|
|Computer in einer anderen Domäne|Nein|Nein|Ja|

 Außerdem:

- Das Konto, unter dem Sie den Visual Studio-Remotedebugdienst ausführen, sollte Administratorrechte auf dem Remotecomputer besitzen, damit alle Prozesse gedebuggt werden können.

- Dem Konto muss auf dem Remotecomputer außerdem mithilfe des Verwaltungstools **Lokale Sicherheitsrichtlinie** die Berechtigung `Log on as a service` gewährt werden.

- Bei Verwendung eines lokalen Kontozugriffs auf den Computer müssen Sie den Visual Studio-Remotedebugdienst unter einem lokalen Konto verwenden.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Stellen Sie sicher, dass der Visual Studio-Remotedebugdienst ordnungsgemäß auf dem Remotecomputer eingerichtet ist. Weitere Informationen finden Sie unter [Remote Debuggen](../debugger/remote-debugging.md).

2. Führen Sie den Remotedebugdienst unter einem Konto aus, über das auf den Hostcomputer des Debuggers zugegriffen werden kann (siehe obige Tabelle).

### <a name="to-add-log-on-as-a-service-privilege"></a>So fügen Sie die Berechtigung "Als Dienst anmelden" hinzu

1. Klicken Sie im Menü **Start** auf **Systemsteuerung**.

2. Wählen Sie in der Systemsteuerung die **Klassische Ansicht** aus (falls erforderlich).

3. Doppelklicken Sie auf **Verwaltung**.

4. Doppelklicken Sie im Fenster „Verwaltung“ auf **Lokale Sicherheitsrichtlinie**.

5. Erweitern Sie im Fenster **Lokale Sicherheitseinstellungen** den Ordner **Lokale Richtlinien**.

6. Klicken Sie auf **Zuweisen von Benutzerrechten**.

7. Doppelklicken Sie in der Spalte **Richtlinie** auf **Anmelden als Dienst**, um sich im Dialogfeld **Anmelden als Dienst** die aktuell zugewiesenen lokalen Gruppenrichtlinien anzeigen zu lassen.

8. Klicken Sie auf die Schaltfläche **Benutzer oder Gruppe hinzufügen**, um neue Benutzer hinzuzufügen.

9. Klicken Sie auf **OK**, wenn Sie fertig sind.

### <a name="to-work-around-this-error"></a>So umgehen Sie diesen Fehler

- Führen Sie den Remotedebugmonitor als Anwendung statt als Dienst aus.

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
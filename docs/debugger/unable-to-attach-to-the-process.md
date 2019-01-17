---
title: Anfügen an den Prozess nicht möglich | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: affcff981ee516810f2ed9f6c2337c5145ebc572
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "53819574"
---
# <a name="unable-to-attach-to-the-process"></a>Anfügen an den Prozess nicht möglich
Anfügen an den Prozess nicht möglich. Der Debuggerkomponente auf dem Server wurde beim Herstellen einer Verbindung zu diesem Computer der Zugriff verweigert.  
  
 Es gibt zwei gängige Szenarios, durch die dieser Fehler verursacht wird:  
  
 Szenario Computer A wird Windows XP ausgeführt. Auf Computer B wird Windows Server 2003 ausgeführt. Die Registrierung auf Computer B enthält den folgenden DWORD-Wert:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Benutzer 1 startet eine Terminal Server-Sitzung (Sitzung 1) auf Computer B und ruft in dieser Sitzung eine verwaltete Anwendung auf.  
  
 Benutzer 2, Administrator beider Computer ist, ist bei Computer a angemeldet. Von dort aus versucht er für die Verbindung zu einer Anwendung, die auf Computer b in Sitzung 1 ausgeführt  
  
 Szenario Ein Benutzer hat auf zwei Computern, A und B in derselben Arbeitsgruppe, angemeldet mit dem gleichen Kennwort auf beiden Computern. Der Debugger auf Computer A ausgeführt wird und versucht, Anfügen an eine verwaltete Anwendung, die auf Computer b-Computer ein **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** festgelegt **Gast**.  
  
### <a name="to-solve-scenario-1"></a>So lösen Sie Szenario 1  
  
-   Führen Sie den Debugger und die verwaltete Anwendung unter Verwendung desselben Benutzerkontonamens und Kennworts aus.  
  
### <a name="to-solve-scenario-2"></a>So lösen Sie Szenario 2  
  
1.  Wählen Sie im Menü **Start** die **Systemsteuerung** aus.  
  
2.  Doppelklicken Sie in der Systemsteuerung auf **Verwaltung**.  
  
3.  Doppelklicken Sie im Fenster „Verwaltung“ auf **Lokale Sicherheitsrichtlinie**.  
  
4.  Wählen Sie im Fenster „Lokale Sicherheitsrichtlinie“ die Option **Lokale Richtlinien**.  
  
5.  In der **Richtlinien** Spalte doppelklicken Sie auf **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
6.  In der **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** Dialogfeld ändern, die lokale sicherheitseinstellung **klassischen**, und klicken Sie auf **OK**.  
  
    > [!CAUTION]
    >    Das Ändern des Sicherheitsmodells in Klassisch kann zu unerwünschtem Zugriff auf freigegebene Dateien und DCOM-Komponenten führen. Wenn Sie diese Änderung vornehmen, kann sich ein Remotebenutzer mit Ihrem lokalen Benutzerkonto anstatt als Gast authentifizieren. Wenn ein Remotebenutzer Ihren Benutzernamen und Ihr Kennwort angibt, kann dieser Benutzer auf alle von Ihnen freigegebenen Ordner und DCOM-Objekte zugreifen. Um nicht autorisierte Zugriffe bei der Verwendung dieses Sicherheitsmodells zu vermeiden, sollten Sie dafür sorgen, dass alle Benutzerkonten auf dem Computer über sichere Kennwörter verfügen, oder richten Sie einen isolierten Netzwerkabschnitt für zu debuggende Computer und die Computer ein, auf denen das Debuggen ausgeführt wird.  
  
7.  Schließen Sie alle Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
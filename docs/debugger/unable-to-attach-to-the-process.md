---
title: Kann nicht an den Prozess angefügt werden soll. | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: a7929be0825ec16ba7e3b6d594dfd96ee6a4dfb6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="unable-to-attach-to-the-process"></a>Anfügen an den Prozess nicht möglich
Anfügen an den Prozess nicht möglich. Der Debuggerkomponente auf dem Server wurde beim Herstellen einer Verbindung zu diesem Computer der Zugriff verweigert.  
  
 Es gibt zwei gängige Szenarios, durch die dieser Fehler verursacht wird:  
  
 **Szenario 1:** Computer A wird Windows XP ausgeführt. Auf Computer B wird Windows Server 2003 ausgeführt. Die Registrierung auf Computer B enthält den folgenden DWORD-Wert:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Benutzer 1 startet eine Terminal Server-Sitzung (Sitzung 1) auf Computer B und ruft in dieser Sitzung eine verwaltete Anwendung auf.  
  
 Benutzer 2, der Administrator beider Computer ist, ist bei Computer a angemeldet. Von dort aus versucht er für die Verbindung zu einer Anwendung auf Computer b in Sitzung 1 ausgeführt  
  
 **Szenario 2:** auf zwei Computern, A und B in der gleichen Arbeitsgruppe ein Benutzer angemeldet ist, mit dem gleichen Kennwort auf beiden Computern. Der Debugger wird auf Computer A ausgeführt und versucht, für die Verbindung zu einer verwalteten Anwendung auf Computer b-Computer A ausgeführten **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** festgelegt **Gast**.  
  
### <a name="to-solve-scenario-1"></a>So lösen Sie Szenario 1  
  
-   Führen Sie den Debugger und die verwaltete Anwendung unter Verwendung desselben Benutzerkontonamens und Kennworts aus.  
  
### <a name="to-solve-scenario-2"></a>Lösen Sie Szenario 2  
  
1.  Aus der **starten** Menü wählen **Systemsteuerung**.  
  
2.  In der Systemsteuerung, doppelklicken Sie auf **Verwaltung**.  
  
3.  Doppelklicken Sie im Verwaltungsfenster auf **lokale Sicherheitsrichtlinie**.  
  
4.  Wählen Sie in das Fenster "Lokale Sicherheitsrichtlinie" **lokale Richtlinien**.  
  
5.  In der **Richtlinien** Spalte doppelklicken Sie auf **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
6.  In der **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** Dialogfeld Feld, ändern Sie die lokale sicherheitseinstellung in **klassischen**, und klicken Sie auf **OK**.  
  
    > [!CAUTION]
    >    Das Ändern des Sicherheitsmodells in Klassisch kann zu unerwünschtem Zugriff auf freigegebene Dateien und DCOM-Komponenten führen. Wenn Sie diese Änderung vornehmen, kann sich ein Remotebenutzer mit Ihrem lokalen Benutzerkonto anstatt als Gast authentifizieren. Wenn ein Remotebenutzer Ihren Benutzernamen und Ihr Kennwort angibt, kann dieser Benutzer auf alle von Ihnen freigegebenen Ordner und DCOM-Objekte zugreifen. Um nicht autorisierte Zugriffe bei der Verwendung dieses Sicherheitsmodells zu vermeiden, sollten Sie dafür sorgen, dass alle Benutzerkonten auf dem Computer über sichere Kennwörter verfügen, oder richten Sie einen isolierten Netzwerkabschnitt für zu debuggende Computer und die Computer ein, auf denen das Debuggen ausgeführt wird.  
  
7.  Schließen Sie alle Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
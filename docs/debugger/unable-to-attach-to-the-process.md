---
title: "Anf&#252;gen an den Prozess nicht m&#246;glich | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.unable2attach"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anf&#252;gen an den Prozess nicht m&#246;glich
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Anfügen an den Prozess nicht möglich.Der Debuggerkomponente auf dem Server wurde beim Herstellen einer Verbindung zu diesem Computer der Zugriff verweigert.  
  
 Es gibt zwei gängige Szenarios, durch die dieser Fehler verursacht wird:  
  
 **Szenario 1:** Auf Computer A wird Windows XP ausgeführt.  Auf Computer B wird Windows Server 2003 ausgeführt.  Die Registrierung auf Computer B enthält den folgenden DWORD\-Wert:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Benutzer 1 startet eine Terminal Server\-Sitzung \(Sitzung 1\) auf Computer B und ruft in dieser Sitzung eine verwaltete Anwendung auf.  
  
 Benutzer 2, der Administrator beider Computer ist, ist bei Computer A angemeldet.  Von dort aus versucht er, eine Verbindung mit einer Anwendung herzustellen, die auf Computer B in Sitzung 1 ausgeführt wird.  
  
 **Szenario 2:** Ein Benutzer hat sich in derselben Arbeitsgruppe unter Verwendung desselben Kennworts bei zwei Computern \(A und B\) angemeldet.  Der Debugger wird auf Computer A ausgeführt und versucht, eine Verbindung zu einer verwalteten Anwendung auf Computer B herzustellen.  Für **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** wurde auf Computer A das Benutzerkonto **Gast** erstellt.  
  
### So lösen Sie Szenario 1  
  
-   Führen Sie den Debugger und die verwaltete Anwendung unter Verwendung desselben Benutzerkontonamens und Kennworts aus.  
  
### So lösen Sie Szenario 2  
  
1.  Aktivieren Sie über das Menü **Start** die **Systemsteuerung**.  
  
2.  Doppelklicken Sie in der Systemsteuerung auf **Verwaltung**.  
  
3.  Doppelklicken Sie im Fenster Verwaltung auf **Lokale Sicherheitsrichtlinie**.  
  
4.  Wählen Sie im Fenster Lokale Sicherheitsrichtlinie die Option **Lokale Richtlinien**.  
  
5.  Doppelklicken Sie in der Spalte **Richtlinien** auf die Option **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
6.  Ändern Sie im Dialogfeld **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** die lokale Sicherheitseinstellung in **Klassisch**, und klicken Sie auf **OK**.  
  
    > [!CAUTION]
    >  Das Ändern des Sicherheitsmodells in Klassisch kann zu unerwünschtem Zugriff auf freigegebene Dateien und DCOM\-Komponenten führen.  Wenn Sie diese Änderung vornehmen, kann sich ein Remotebenutzer mit Ihrem lokalen Benutzerkonto anstatt als Gast authentifizieren.  Wenn ein Remotebenutzer Ihren Benutzernamen und Ihr Kennwort angibt, kann dieser Benutzer auf alle von Ihnen freigegebenen Ordner und DCOM\-Objekte zugreifen.  Um nicht autorisierte Zugriffe bei der Verwendung dieses Sicherheitsmodells zu vermeiden, sollten Sie dafür sorgen, dass alle Benutzerkonten auf dem Computer über sichere Kennwörter verfügen, oder richten Sie einen isolierten Netzwerkabschnitt für zu debuggende Computer und die Computer ein, auf denen das Debuggen ausgeführt wird.  
  
7.  Schließen Sie alle Fenster.  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)
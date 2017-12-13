---
title: "Problembehandlung und bekannte Probleme (Visual Studio-Tools für Unity) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: a0b5f9c4e3be1c9f54fe9c15a6f741516b3dbdc9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Problembehandlung und bekannte Probleme (Visual Studio-Tools für Unity)
In diesem Abschnitt finden Sie Lösungen für häufige Probleme mit Visual Studio-Tools für Unity und Beschreibungen bekannter Probleme. Außerdem erfahren Sie, wie Sie Visual Studio-Tools für Unity verbessern können, indem Sie Fehler melden.  
  
## <a name="troubleshooting"></a>Problembehandlung  
In den folgenden Abschnitten finden Sie Informationen zum Beheben häufiger Probleme mit Visual Studio-Tools für Unity.  

### <a name="visual-studio-crashes"></a>Visual Studio stürzt ab
Dies kann daran liegen, dass der MEF-Cache für Visual Studio beschädigt ist.

Sie müssen den folgenden Ordner entfernen, um den MEF-Cache zurückzusetzen (bitte schließen Sie Visual Studio, bevor Sie dies tun):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Dadurch sollte das Problem behoben werden. Wenn Sie immer noch auf Probleme stoßen sollten, führen Sie eine Developer-Eingabeaufforderung für Visual Studio als Administrator aus, und verwenden Sie den folgenden Befehl:

```batch
 devenv /setup
```

### <a name="issues-with-vs2015-and-intellisense-or-code-coloration"></a>Probleme mit Visual Studio 2015 und IntelliSense oder der Codeeinfärbung.
Sie sollten Ihre Version von Visual Studio 2015 auf Update 3 aktualisieren. 

### <a name="visual-studio-hangs"></a>Visual Studio reagiert nicht mehr
Mehrere Unity-Plug-Ins wie Parse, FMOD, UMP (Universal Media Player), ZFBrowser oder Embedded Browser verwenden native Threads. Wenn ein Plug-In der Runtime einen nativen Thread hinzufügt, führt dies zu einem Problem, da die Runtime dann Blockierungsaufrufe an das Betriebssystem ausgibt. Das bedeutet, dass Unity den Thread für den Debugger (oder das Neuladen einer Domäne) nicht unterbrechen kann und nicht mehr reagiert. 

Für FMOD gibt es eine Möglichkeit zur Problemumgehung: Sie können das Initialisierungs-[Flag](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE weitergeben, um die asynchrone Verarbeitung zu deaktivieren und diese gesamte Verarbeitung auf dem Haupthread durchzuführen.

### <a name="incompatible-project-in-visual-studio"></a>Nicht kompatibles Projekt in Visual Studio
Überprüfen Sie zunächst, ob Visual Studio als externer Skript-Editor in Unity festgelegt ist (Bearbeiten > Einstellungen > Externe Tools). Überprüfen Sie anschließend, dass das Visual Studio-Plug-In in Unity installiert ist (die Felder „Hilfe“ bzw. „Info“ müssen in der Ansicht im unteren Bereich eine Nachricht wie „Microsoft Visual Studio Tools für Unity ist aktiviert“ anzeigen). Überprüfen Sie dann, ob die Erweiterung korrekt in Visual Studio installiert wurde (Hilfe bzw. Info).

### <a name="assembly-reference-issues"></a>Probleme mit dem Assemblyverweis
Wenn Ihr Projekt im Hinblick auf Verweise komplex ist, oder wenn Sie diesen Generationsschritt besser steuern möchten, können Sie unsere [API](../cross-platform/customize-project-files-created-by-vstu.md) verwenden, um das generierte Projekt oder den Projektmappeninhalt zu bearbeiten. Sie können auch [Antwortdateien](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) in Ihrem Unity-Projekt verwenden, die dann verarbeitet werden.

### <a name="breakpoints-with-a-warning"></a>Haltepunkte mit einer Warnung
Wenn Visual Studio keinen Quellspeicherort für einen bestimmten Haltepunkt finden kann, wird Ihnen eine Warnung um Ihren Haltepunkt angezeigt. Überprüfen Sie, ob das von Ihnen verwendete Verhalten in der Unity-Szene korrekt geladen bzw. verwendet wird. 

### <a name="breakpoints-not-hit"></a>Haltepunkte werden nicht erreicht.
 Überprüfen Sie, ob das von Ihnen verwendete Verhalten in der Unity-Szene korrekt geladen bzw. verwendet wird. Beenden Sie Visual Studio und Unity, und löschen Sie anschließend alle generierten Dateien (*.csproj, *.sln) sowie den gesamten Bibliotheksordner.

### <a name="unable-to-attach"></a>Anfügen nicht möglich.
-   Versuchen Sie, Ihr Antivirenprogramm kurzzeitig zu deaktivieren, oder erstellen Sie Ausschlussregeln für Visual Studio und Unity.
-   Versuchen Sie, Ihre Firewall kurzzeitig zu deaktivieren, oder erstellen Sie Regeln, um das TCP/UDP-Netzwerken zwischen Visual Studio und Unity zuzulassen. 
-   Wir haben festgestellt, dass Programme wie Team Viewer die Prozesserkennung beeinträchtigen. Sie können versuchen, jegliche zusätzliche Software kurzzeitig zu unterbrechen, um zu prüfen, ob sich dadurch etwas ändert.

### <a name="unable-to-debug-android-players"></a>Debuggen von Android Players nicht möglich
Multicast wird für die Erkennung von Players (der von Unity verwendete Standardmechanismus) verwendet. Anschließend wird allerdings eine gewöhnliche TCP-Verbindung verwendet, um den Debugger anzufügen. Die Erkennungsphase stellt für Android-Geräte das größte Problem dar. 

USB ist eine sehr schnelle Möglichkeit zum Debuggen. Allerdings ist diese Methode nicht mit dem Erkennungsmechanismus des Unity-Players kompatibel.
WLAN ist zwar vielseitiger, aber aufgrund der Wartezeit extrem langsam im Vergleich zu USB. Es wurde mangelnde Unterstützung für einige Router oder Geräte festgestellt (die Nexus-Serien sind dafür besonders bekannt). 

Sie können versuchen, den folgenden USB zu verwenden, um die geöffneten Ports auf dem verbundenen Gerät anzuzeigen (wenn der Player verfügbar ist und ausgeführt wird, sodass Sie den Port zum Debuggen immer im Format 56xxx sehen können):

```shell  
adb shell netstat
```  

Leiten Sie den Port an den lokalen Computer weiter:

```shell  
adb forward tcp:56xxx tcp:56xxx
```  

Verbinden Sie anschließend Visual Studio-Tools für Unity über den weitergeleiteten Port 127.0.0.1:56xxx.

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrieren von UnityVS zu Visual Studio-Tools für Unity  
 Wenn Sie von UnityVS zu Visual Studio-Tools für Unity migrieren, müssen Sie neue Visual Studio-Projektmappen für Ihre Unity-Projekte generieren.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>So migrieren Sie Ihr Unity-Projekt von UnityVS 1.8 zu Visual Studio-Tools für Unity 1.9  
  
1.  Löschen Sie die alten Projektmappen- und Projektdateien aus Ihrem Unity-Projekt. Suchen Sie im Stammverzeichnis Ihres Unity-Projekts die SLN- und PROJ-Dateien von Visual Studio, und löschen Sie alle.  
  
2.  Importieren Sie das Visual Studio-Tools für Unity-Paket in Ihr Unity-Projekt. Informationen zum Importieren des VSTU-Pakets finden Sie unter "Konfigurieren von Visual Studio-Tools für Unity" auf der Seite [Erste Schritte](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  
  
3.  Generieren Sie neue Projektmappen- und Projektdateien. Wenn Sie sie jetzt generieren möchten, klicken Sie im Unity-Editor im Hauptmenü auf **Visual Studio Tools**, **Generate Project Files**. Andernfalls können Sie diesen Schritt nach Wunsch überspringen. Visual Studio-Tools für Unity generiert die neuen Dateien automatisch, wenn Sie auf **Visual Studio Tools**, **Open in Visual Studio**klicken.  
  
### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Unter Windows fordert Visual Studio das Herunterladen des Unity-Zielframeworks an.  
 Visual Studio-Tools für Unity erfordert .NET Framework 3.5, das nicht standardmäßig unter Windows 8 oder 10 installiert ist. Um dieses Problem zu beheben, befolgen Sie die Anweisungen zum Herunterladen und Installieren von .NET Framework 3.5.  
  
## <a name="known-issues"></a>Bekannte Probleme  
 Es gibt bekannte Probleme in Visual Studio-Tools für Unity, deren Ursache die Interaktion des Debuggers mit der älteren Version von Unity des C#-Compilers ist. Wir arbeiten daran, diese Fehler zu beheben, aber in der Zwischenzeit können die folgenden Probleme weiterhin auftreten:  
  
-   Beim Debuggen stürzt Unity manchmal ab.  
  
-   Beim Debuggen friert Unity manchmal ein.  
  
-   Bei Einzel- und Prozedurschritten für Methoden kommt es mitunter zu einem Fehlverhalten, insbesondere bei Iteratoren oder innerhalb von Switch-Anweisungen.  
  
## <a name="reporting-errors"></a>Erstellen von Fehlerberichten  
 Helfen Sie uns, die Qualität von Visual Studio-Tools für Unity zu verbessern, indem Sie Fehlerberichte senden, sollte das Programm abstürzen, einfrieren oder ein anderer Fehler auftreten. Dies hilft uns beim Untersuchen und Beheben von Problemen in Visual Studio-Tools für Unity. Vielen Dank!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Wie Sie einen Fehler melden, wenn Visual Studio einfriert  
 Uns wurde gemeldet, dass Visual Studio beim Debuggen mit Visual Studio-Tools für Unity mitunter einfriert, aber wir benötigen mehr Daten, um dieses Problem zu verstehen. Sie können uns bei der Untersuchung helfen, indem Sie die folgenden Schritte ausführen.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>So melden Sie, dass Visual Studio beim Debuggen mit Visual Studio-Tools für Unity einfriert

*Unter Windows:*  

1.  Öffnen Sie eine Instanz von Visual Studio.
  
2.  Öffnen Sie das Dialogfeld "An den Prozess anhängen". Wählen Sie in der neuen Instanz von Visual Studio im Hauptmenü **Debuggen**, **An den Prozess anhängen**.  
  
3.  Hängen Sie den Debugger an die eingefrorene Instanz von Visual Studio an. Wählen Sie im Dialogfeld **An den Prozess anhängen** die eingefrorene Instanz von Visual Studio in der Tabelle **Verfügbare Prozesse** aus, und klicken Sie dann auf die Schaltfläche **Anhängen** .  
  
4.  Halten Sie den Debugger an. Klicken Sie in der neuen Instanz von Visual Studio im Hauptmenü auf **Debuggen**, **Alle unterbrechen**, oder drücken Sie **STRG+ALT+UNTRBR**.  
  
5.  Erstellen Sie einen Thread-Dump. Geben Sie im Befehlsfenster den folgenden Befehl ein, und drücken Sie die **EINGABETASTE**:  
  
    ```powershell  
    Debug.ListCallStack /AllThreads /ShowExternalCode  
    ```  
  
    Möglicherweise müssen Sie zuerst das Fenster **Befehl** einblenden. Wählen Sie in Visual Studio im Hauptmenü **Ansicht**, **Weitere Fenster**, **Befehlsfenster**.  

*Unter Mac:*

1. Öffnen Sie ein Terminal, und rufen Sie die PID von Visual Studio für Mac ab:

    ```shell  
    ps aux | grep "[V]isual Studio.app"
    ``` 

1. Starten Sie den LLDB-Debugger:

    ```shell  
    lldb
    ``` 

1. Führen Sie eine Anfügung an die Visual Studio für Mac-Instanz durch:

    ```shell  
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ``` 

1. Rufen Sie StackTrace für alle Threads ab:

    ```shell  
    bt all
    ```

Senden Sie zum Schluss den Thread-Dump an [vstusp@microsoft.com](mailto:vstusp@microsoft.com)zusammen mit einer Beschreibung, was Sie gerade getan haben, als Visual Studio eingefroren ist.


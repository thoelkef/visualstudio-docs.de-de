---
title: Visual Studio für Mac – Integriertes Terminal
description: Visual Studio für Mac bietet eine integrierte Entwicklungsumgebung zum Erstellen von .NET-Anwendungen unter macOS. Dazu gehören ASP.NET Core-Websites und Xamarin-Projekte für iOS, Android, Mac und Xamarin.Forms.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: d362938e8f0075591ea5d4ed8461d11395680b5c
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185674"
---
# <a name="integrated-terminal"></a>Integriertes Terminal
In Visual Studio für Mac können Sie ein integriertes Terminal öffnen und am Stamm Ihrer Projektmappe beginnen. Das Terminal kann in verschiedenen Situationen nützlich sein: Ausführen von Front-End-Aufgaben (Beispiel.: npm, ng oder vue), Verwalten von Containern, Ausführen erweiterter Git-Befehle, Ausführen von Entity Framework-Befehlen, Anzeigen der Dotnet-CLI-Ausgabe, Hinzufügen von NuGet-Paketen und vieles mehr. 

So öffnen Sie das Terminal:
- Verwenden Sie die Tastenkombination **STRG+'** , um das Terminalfenster anzuzeigen oder auszublenden.
- Verwenden Sie das Menü **Ansicht** \> **Pads**  \> **Terminal**.
- Verwenden Sie den Befehl **terminal** in der Suchleiste.

![*Das integrierte Terminal von Visual Studio für Mac unmittelbar nach dem Start.*](media/integrated-terminal-intro.png)

Wenn das Terminal gestartet wird, werden standardmäßig folgende Aktionen durchführt:
- Festlegen des Arbeitsverzeichnisses auf den Pfad der aktuellen Projektmappe.
- Laden der Standardsystemshell.

## <a name="search"></a>Suchen
Sie können den Inhalt des Terminalfensters durchsuchen, indem Sie das Menü **Suche > Suchen...** verwenden.

![*Suchbenutzeroberfläche im integrierten Terminal von Visual Studio für Mac*](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Tastenkombinationen des Terminals
|Befehle|Tastenkombinationen|
|-|-|
|Anzeigen/Ausblenden des Terminalfensters|**STRG+`**|
|Erstellen einer neuen Terminalinstanz|**STRG+'**|
|Bildlauf nach oben für Seite|**BildAuf**|
|Bildlauf nach unten für Seite|**BildAb**|
|Durchlaufen zuvor verwendeter Befehle|**↑**, **↓**|
|Vergrößern des Schriftgrads|**⌘+**|
|Verkleinern des Schriftgrads|**⌘-**|

## <a name="multiple-instances"></a>Mehrfache Instanzen
Mehrere Instanzen des Terminals können jederzeit ausgeführt werden. Sie können eine neue-Instanz erstellen, indem Sie die Tastenkombination **STRG+'** verwenden. Sie können zwischen Instanzen wechseln, indem Sie auf die Registerkarte für jede Instanz klicken oder die Tastenkombination **STRG+TAB** verwenden, um das Dialogfeld „Fensterauswahl“ zu öffnen.

![*Mehrere Terminalinstanzen in Visual Studio für Mac*](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Anpassen des Terminalfensters
### <a name="configuring-the-terminal-font"></a>Konfigurieren der Schriftart des Terminals
Sie können die Schriftart und die den Schriftgrad im Bereich „Einstellungen > Umgebung > Schriftarten“ ändern, die für Terminalinhalte verwendet werden. Standardmäßig ist die Schriftart mit der des Ausgabepadinhalts identisch. Es wird Menlo Regular, Größe 11 verwendet. Sie können eine beliebige Schriftart unabhängig von der Schriftart des Editors festlegen.

![*Anpassen der Schriftarteinstellungen für das integrierte Terminal*](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Wiederverwenden von Systemterminalanpassungen
Das integrierte Terminal verwendet dieselben Standardwerte und dieselbe Konfiguration wie das macOS-Systemterminal. Dies bedeutet, dass Ihre Terminalanpassungen (zsh, oh-my-zsh usw.) auch im integrierten Terminal funktionieren.

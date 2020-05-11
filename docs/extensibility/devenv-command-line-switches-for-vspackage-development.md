---
title: Devenv Command-Line Switches für die VSPackage-Entwicklung | Microsoft Docs
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712190"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Devenv-Befehlszeilenschalter für die VSPackage-Entwicklung

Visual Studio ermöglicht Entwicklern, Aufgaben über die `devenv.exe`Befehlszeile zu automatisieren, wenn sie die Datei ausführen, die die Visual Studio-IDE startet.

 Zu den Aufgaben gehören:

- Bereitstellen von Anwendungen in vordefinierten Konfigurationen von außerhalb der IDE.

- Automatisches Erstellen von Projekten mithilfe voreingestellter Buildeinstellungen oder Debugkonfigurationen.

- Laden der IDE in bestimmten Konfigurationen, alle von außerhalb der IDE. Sie können die IDE auch beim Start anpassen.

## <a name="guidelines-for-switches"></a>Richtlinien für Switches

In der Visual Studio-Dokumentation werden die Befehlszeilenwechsel auf Benutzerebene `devenv` beschrieben. Weitere Informationen finden Sie unter [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md). Das `devenv` Tool unterstützt auch zusätzliche Befehlszeilen-Switches, die bei der ENTWICKLUNG, Bereitstellung und dem Debuggen von VSPackage nützlich sind.

| Befehlszeilenschalter | BESCHREIBUNG |
|---------------------| - |
| `/ResetSkipPkgs` | Löscht alle Optionen zum Laden über überspringen, die von Benutzern hinzugefügt wurden, die das Laden problematischer VSPackages vermeiden möchten, und startet dann Visual Studio. Das Vorhandensein eines SkipLoading-Tags deaktiviert das Laden eines VSPackage. Das Löschen des Tags ermöglicht das Laden des VSPackage erneut.<br /><br /> Der Schalter verwendet keine Argumente. |
| `/RootSuffix` | Startet Visual Studio mithilfe eines alternativen Speicherorts. Der folgende Befehl wird von der Vom Visual Studio SDK-Installationsprogramm erstellten Verknüpfung ausgeführt:<br /><br /> `devenv /RootSuffix exp`<br /><br /> Identifiziert in `exp` diesem Fall einen Speicherort mit einem bestimmten `10.0Exp` Suffix (z. B. anstelle von `10.0`). Mit der experimentellen Instanz können Sie ein VSPackage getrennt von der Instanz von Visual Studio debuggen, die Sie zum Schreiben von Code verwenden.<br /><br /> Dieser Schalter kann eine beliebige Zeichenfolge verwenden, die einen Speicherort identifiziert, den Sie mithilfe von VSRegEx.exe erstellt haben. Weitere Informationen finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Startet Visual Studio im abgesicherten Modus und lädt nur die Standard-IDE und Dienste. Der `/SafeMode` Switch verhindert, dass alle VSPackages von Drittanbietern beim Starten von Visual Studio geladen werden, wodurch eine stabile Ausführung gewährleistet wird.<br /><br /> Der Schalter verwendet keine Argumente. |
| `/Setup` | Erzwingt, dass Visual Studio Ressourcenmetadaten zusammenführt, die Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages beschreiben. Sie können diesen Befehl nur als Administrator ausführen. <br /><br /> Der Schalter verwendet keine Argumente. Der Befehl `devenv /Setup` wird in der Regel als letzter Schritt der Installation angegeben. Durch die `/Setup` Verwendung des Schalters wird die IDE nicht gestartet.|
| `/Splash` | Zeigt wie gewohnt den Visual Studio-Begrüßungsbildschirm an und zeigt dann ein Meldungsfeld an, bevor die Haupt-IDE angezeigt wird. Mit dem Meldungsfeld können Sie den Begrüßungsbildschirm untersuchen (z. B. um nach einem VSPackage-Produktsymbol zu suchen).<br /><br /> Der Schalter verwendet keine Argumente. |

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Befehlszeilenschaltern](../extensibility/adding-command-line-switches.md)
- [Devenv-Befehlszeilenparameter](../ide/reference/devenv-command-line-switches.md)

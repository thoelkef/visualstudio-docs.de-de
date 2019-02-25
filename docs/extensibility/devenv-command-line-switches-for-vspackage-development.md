---
title: Devenv-Befehlszeilenschalter für die Entwicklung von VSPackage | Microsoft-Dokumentation
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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd95fe31949b51c7167337ad21c51251e84a19a7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705530"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Devenv-Befehlszeilenschalter für die Entwicklung von VSPackages

Visual Studio können Entwickler über die Befehlszeile automatisieren Ausführung `devenv.exe`, die Datei, die Visual Studio-IDE wird gestartet.

 Tasks gehört Folgendes:

- Bereitstellen von Anwendungen in vordefinierten Konfigurationen von außerhalb der IDE aus.

- Erstellen von Projekten mit der Voreinstellung wird automatisch Buildeinstellungen oder Debugkonfigurationen.

- Laden die IDE in spezifischen Konfigurationen außerhalb der IDE aus. Sie können auch die IDE beim Start anpassen.

## <a name="guidelines-for-switches"></a>Richtlinien für switches

Visual Studio-Dokumentation beschreibt die Benutzerebene `devenv` Befehlszeilenschalter. Weitere Informationen finden Sie unter [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md). Die `devenv` Tool unterstützt auch zusätzliche Befehlszeilenoptionen, die mit der VSPackage-Entwicklung, Bereitstellung und Debuggen hilfreich sind.

| Befehlszeilenschalter | Beschreibung |
|---------------------| - |
| `/ResetSkipPkgs` | Löscht alle Skip-Loading-Optionen, die von Benutzern, die Laden von problematischen VSPackages verhindern möchten hinzugefügt wurden, und klicken Sie dann startet Visual Studio. Das Vorhandensein eines SkipLoading-Tags deaktiviert das Laden eines VSPackage. Das Löschen des Tags das Laden des VSPackage erneut aktiviert werden.<br /><br /> Der Schalter verwendet keine Argumente. |
| `/RootSuffix` | Startet Visual Studio mit einem alternativen Speicherort. Der folgende Befehl wird die Verknüpfung erstellt, die vom Visual Studio SDK-Installationsprogramm ausgeführt:<br /><br /> `devenv /RootSuffix exp`<br /><br /> In diesem Fall `exp` identifiziert einen Speicherort mit einem bestimmten Suffix (z. B. `10.0Exp` anstelle von `10.0`). Die experimentelle Instanz können Sie eine VSPackage getrennt von der Instanz von Visual Studio zu debuggen, die Sie verwenden, um Code zu schreiben.<br /><br /> Dieser Schalter dauert eine beliebige Zeichenfolge, die einen Speicherort angibt, den Sie mithilfe von VSRegEx.exe erstellt haben. Weitere Informationen finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Startet Visual Studio im abgesicherten Modus Laden nur die Standard-IDE und die Dienste an. Die `/SafeMode` Schalter verhindert, dass alle VSPackages von Drittanbietern geladen werden, wenn der Start von Visual Studio stabile Ausführung sicherzustellen.<br /><br /> Der Schalter verwendet keine Argumente. |
| `/Setup` | Erzwingt, dass Visual Studio, um die Ressourcenmetadaten, die Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages beschreibt. Sie können diesen Befehl nur als Administrator ausführen. <br /><br /> Der Schalter verwendet keine Argumente. Der Befehl `devenv /Setup` wird in der Regel als letzter Schritt der Installation angegeben. Verwenden der `/Setup` Switch nicht starten Sie die IDE.|
| `/Splash` | Zeigt den Begrüßungsbildschirm für Visual Studio, Bildschirm wie üblich, und klicken Sie dann zeigt die Meldung vor dem Anzeigen der Haupt-IDE Feld. Das Meldungsfeld können Sie die Studie des Begrüßungsbildschirm (z. B. zu prüfen, ein VSPackage-Produkt-Symbol).<br /><br /> Der Schalter verwendet keine Argumente. |

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Befehlszeilenschaltern](../extensibility/adding-command-line-switches.md)
- [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)
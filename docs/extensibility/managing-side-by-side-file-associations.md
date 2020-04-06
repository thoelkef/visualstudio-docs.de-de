---
title: Verwalten von Side-by-Side-Dateizuordnungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702764"
---
# <a name="manage-side-by-side-file-associations"></a>Verwalten von seitenebenigen Dateizuordnungen

Wenn Ihr VSPackage Dateizuordnungen bereitstellt, müssen Sie entscheiden, wie nebeneinander Installationen behandelt werden sollen, bei denen eine bestimmte Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Öffnen einer Datei aufgerufen werden soll. Inkompatible Dateiformate verschlimmern das Problem.

Benutzer erwarten, dass eine neue Version eines Produkts mit früheren Versionen kompatibel ist, sodass vorhandene Dateien in einer neuen Version geladen werden können, ohne Daten zu verlieren. Idealerweise kann Ihr VSPackage die Dateiformate früherer Versionen sowohl laden als auch speichern. Wenn dies nicht zutrifft, sollten Sie anbieten, das Dateiformat auf die neue Version Ihres VSPackage zu aktualisieren. Der Nachteil dieses Ansatzes ist, dass die aktualisierte Datei in der früheren Version nicht geöffnet werden kann.

Um dieses Problem zu vermeiden, können Sie Erweiterungen ändern, wenn Dateiformate inkompatibel werden. Beispielsweise könnte Version 1 Ihres VSPackage die Erweiterung *.mypkg10*und Version 2 die Erweiterung *.mypkg20*verwenden. Dieser Unterschied identifiziert das VSPackage, das eine bestimmte Datei öffnet. Wenn Sie neuere VSPackages zur Liste der Programme hinzufügen, die einer alten Erweiterung zugeordnet sind, können Benutzer mit der rechten Maustaste auf die Datei klicken und sie in einem neueren VSPackage öffnen. An diesem Punkt kann Ihr VSPackage anbieten, die Datei auf das neue Format zu aktualisieren oder die Datei zu öffnen und die Kompatibilität mit früheren Versionen des VSPackage beizubehalten.

> [!NOTE]
> Sie können diese Ansätze kombinieren. Sie können z. B. Abwärtskompatibilität bieten, indem Sie eine ältere Datei laden und anbieten, das Dateiformat zu aktualisieren, wenn der Benutzer es speichert.

## <a name="face-the-problem"></a>Stellen Sie sich dem Problem

Wenn mehrere nebeneinander vsPackages die gleiche Erweiterung verwenden sollen, müssen Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Version auswählen, die der Erweiterung zugeordnet ist. Hier sind zwei Alternativen:

- Öffnen Sie die Datei [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in der neuesten Version der auf dem Computer eines Benutzers installierten Version.

   Bei diesem Ansatz ist Ihr Installationsprogramm dafür [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verantwortlich, die neueste Version und die für die Dateizuordnung geschriebene Version zu bestimmen und in den Registrierungseintrag einzubeziehen. In einem Windows Installer-Paket können Sie benutzerdefinierte Aktionen zum [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Festlegen einer Eigenschaft einschließen, die die neueste Version von angibt.

  > [!NOTE]
  > In diesem Zusammenhang bedeutet "neueste" "neueste unterstützte Version". Diese Installationseinträge erkennen nicht automatisch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]eine nachfolgende Version von . Einträge in [Detecting System Requirements](../extensibility/internals/detecting-system-requirements.md) und in [Commands That Must Be Run After Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) sind [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ähnlich denen, die hier vorgestellt werden, und müssen zusätzliche Versionen von unterstützen.

   Die folgenden Zeilen in der Tabelle CustomAction legen fest, dass die DEVENV_EXE_LATEST Eigenschaft eine Eigenschaft ist, die von den Tabellen AppSearch und RegLocator festgelegt wird, die in [Befehlen beschrieben werden und nach](../extensibility/internals/commands-that-must-be-run-after-installation.md)der Installation ausgeführt werden müssen. Zeilen in der Tabelle InstallExecuteSequence planen die benutzerdefinierten Aktionen früh in der Ausführungssequenz. Die Werte in der Spalte Bedingung machen die Logik:

  - Visual Studio .NET 2002 ist die neueste Version, wenn es sich um die einzige aktuelle Version handelt.

  - Visual Studio .NET 2003 ist die neueste [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Version nur, wenn sie vorhanden ist und nicht vorhanden ist.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ist die neueste Version, wenn es die einzige aktuelle Version ist.

    Das Ergebnis ist, dass DEVENV_EXE_LATEST den Pfad der neuesten Version von devenv.exe enthält.

  **CustomAction-Tabellenzeilen, die die neueste Version von Visual Studio bestimmen**

  |Aktion|type|`Source`|Ziel|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallExecuteSequence-Tabellenzeilen, die die neueste Version von Visual Studio bestimmen**

  |Aktion|Bedingung|Sequenz|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 UND NICHT (DEVENV_EXE_2003 ODER DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 UND NICHT DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Sie können die DEVENV_EXE_LATEST-Eigenschaft in der Registrierungstabelle des Windows Installer-Pakets verwenden, um den Standardwert **des HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand-Schlüssels** [DEVENV_EXE_LATEST] "%1" zu schreiben.

- Führen Sie ein freigegebenes Launcher-Programm aus, das die beste Auswahl aus verfügbaren VSPackage-Versionen treffen kann.

   Die Entwickler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] von wählte diesen Ansatz, um die komplexen Anforderungen der verschiedenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Formate von Lösungen und Projekten zu behandeln, die aus vielen Versionen von resultieren. Bei diesem Ansatz registrieren Sie ein Launcherprogramm als Erweiterungshandler. Der Launcher untersucht die Datei und [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] entscheidet, welche Version von und Ihr VSPackage diese bestimmte Datei verarbeiten kann. Wenn ein Benutzer beispielsweise eine Datei öffnet, die zuletzt von einer bestimmten Version Ihres VSPackage gespeichert wurde, kann der Launcher dieses VSPackage in der entsprechenden Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]starten. Darüber hinaus könnte ein Benutzer den Launcher so konfigurieren, dass immer die neueste Version gestartet wird. Ein Launcher kann einen Benutzer auch auffordern, das Format der Datei zu aktualisieren. Wenn das Format der Datei eine Versionsnummer enthält, kann der Launcher einen Benutzer informieren, wenn das Dateiformat aus einer Version stammt, die später als eine oder mehrere der installierten VSPackages ist.

   Der Launcher sollte sich in einer Windows Installer-Komponente befindet, die für alle Versionen Ihres VSPackage freigegeben ist. Dieser Prozess stellt sicher, dass die neueste Version immer installiert ist und nicht entfernt wird, bis alle Versionen Ihres VSPackage deinstalliert wurden. Auf diese Weise bleiben die Dateizuordnungen und andere Registrierungseinträge der Launcher-Komponente erhalten, auch wenn eine Version des VSPackage deinstalliert wird.

## <a name="uninstall-and-file-associations"></a>Deinstallieren und Dateizuordnungen

Durch die Deinstallation eines VSPackage, das Registrierungseinträge für Dateizuordnungen schreibt, werden die Dateizuordnungen entfernt. Daher hat die Erweiterung keine zugeordneten Programme. Windows Installer "stellt" die Registrierungseinträge nicht wieder her, die bei der Installation des VSPackage hinzugefügt wurden. Hier sind einige Möglichkeiten, die Dateizuordnungen eines Benutzers zu beheben:

- Verwenden Sie eine freigegebene Launcherkomponente wie zuvor beschrieben.

- Weisen Sie den Benutzer an, eine Reparatur der Version des VSPackage auszuführen, die der Benutzer für die Dateizuordnung besitzen möchte.

- Stellen Sie ein separates ausführbares Programm bereit, das die entsprechenden Registrierungseinträge neu schreibt.

- Stellen Sie eine Seite oder ein Dialogfeld mit Konfigurationsoptionen bereit, mit dem Benutzer Dateizuordnungen auswählen und verlorene Zuordnungen zurückfordern können. Weisen Sie die Benutzer an, sie nach der Deinstallation auszuführen.

## <a name="see-also"></a>Weitere Informationen

- [Registrieren von Dateinamenerweiterungen für side-by-side-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Register verbs für Dateinamenerweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)

---
title: Befehle, die nach der Installation ausgeführt werden müssen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e85a03c71064687fdfbacf24b7aa59cd2a47f1a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982025"
---
# <a name="commands-that-must-be-run-after-installation"></a>Befehle, die nach der Installation ausgeführt werden müssen
Wenn Sie die Erweiterung über eine *MSI* -Datei bereitstellen, müssen Sie **Devenv/Setup** im Rahmen der Installation ausführen, damit Visual Studio Ihre Erweiterungen ermitteln kann.

> [!NOTE]
> Die Informationen in diesem Thema betreffen das Auffinden von " *devenv. exe* " mit Visual Studio 2008 und früher. Informationen zum Ermitteln von " *devenv. exe* " mit neueren Versionen von Visual Studio finden Sie unter [Erkennen von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Suchen von "" "" "" ".
 Sie können die Datei " *devenv. exe* " der einzelnen Versionen aus Registrierungs Werten suchen, die in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installer schreiben. verwenden Sie dazu die Tabelle "reglocator" und "AppSearch", um die Registrierungs Werte als Eigenschaften zu speichern Weitere Informationen finden Sie unter [Erkennen von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Relocator-Tabellenzeilen, um "devenv. exe" aus verschiedenen Versionen von Visual Studio zu suchen

|Signatur|Fasst|Key|-Name|Geben Sie Folgendes ein:|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|Software\microsoft\visualstudio\7.0\setup\vs|Umgebungs Pfad|2|
|RL_DevenvExe_2003|2|Software\microsoft\visualstudio\7,1 \setup\vs|Umgebungs Pfad|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\setup\vs|Umgebungs Pfad|2|
|RL_DevenvExe_2008|2|Software\Microsoft\VisualStudio\9.0\setup\vs|Umgebungs Pfad|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Hiermit werden Tabellenzeilen für entsprechende reglocator-Tabellenzeilen durchsucht.

|property|Signatur|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Der Visual Studio-Installer schreibt z. b. den Registrierungs Wert **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** als *c:\vs2008\common7\ide\devenv.exe*, einen kompletten Pfad zur ausführbaren Datei. Das Installationsprogramm muss ausgeführt werden.

> [!NOTE]
> Da die Typspalte der reglocator-Tabelle 2 ist, ist es nicht erforderlich, zusätzliche Versionsinformationen in der Signatur Tabelle anzugeben.

## <a name="run-devenvexe"></a>Ausführen von "Debug-v. exe"
 Nachdem die AppSearch-Standardaktion im Installationsprogramm ausgeführt wurde, weist jede Eigenschaft in der AppSearch-Tabelle einen Wert auf, der auf die Datei " *devenv. exe* " für die entsprechende Version von Visual Studio zeigt. Wenn einer der angegebenen Registrierungs Werte nicht vorhanden ist – da diese Version von Visual Studio nicht installiert ist – wird die angegebene Eigenschaft auf NULL festgelegt.

 Windows Installer unterstützt das Ausführen einer ausführbaren Datei, auf die eine Eigenschaft durch den benutzerdefinierten Aktionstyp 50 zeigt. Die benutzerdefinierte Aktion sollte die Skript Ausführungs Optionen `msidbCustomActionTypeInScript` (1024) und `msidbCustomActionTypeCommit` (512) enthalten, um sicherzustellen, dass das VSPackage erfolgreich installiert wurde, bevor es in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integriert wird. Weitere Informationen finden Sie unter [CustomAction Table](/windows/desktop/msi/customaction-table) und [Custom Action in-Script Execution Options](/windows/desktop/msi/custom-action-in-script-execution-options).

 Benutzerdefinierte Aktionen des Typs 50 geben die Eigenschaft an, die die ausführbare Datei als Wert der Quell Spalte und Befehlszeilenargumente in der Ziel Spalte enthält.

### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction-Tabellenzeilen zum Ausführen von "devenv. exe"

|Aktion|Geben Sie Folgendes ein:|Quelle|Target|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Benutzerdefinierte Aktionen müssen in der InstallExecuteSequence-Tabelle erstellt werden, um die Ausführung während der Installation zu planen. Verwenden Sie die entsprechende Eigenschaft in den einzelnen Zeilen der Spalte Bedingung, um zu verhindern, dass die benutzerdefinierte Aktion ausgeführt wird, wenn diese Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht auf dem System installiert ist.

> [!NOTE]
> NULL-Wert Eigenschaften werden zu `False` ausgewertet, wenn Sie in Bedingungen verwendet werden.

 Der Wert der Sequence-Spalte für jede benutzerdefinierte Aktion hängt von anderen Sequenz Werten im Windows Installer Paket ab. Die Sequenzwerte sollten so lauten, dass die benutzerdefinierten Aktionen *devenv. exe* so nah wie möglich ausgeführt werden, unmittelbar vor der Standardaktion InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence-Tabelle, um die benutzerdefinierten Aktionen "devenv. exe" zu planen

|Aktion|Bedingung|Sequenz|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Siehe auch
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
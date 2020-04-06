---
title: Befehle, die nach der Installation ausgeführt werden müssen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709474"
---
# <a name="commands-that-must-be-run-after-installation"></a>Befehle, die nach der Installation ausgeführt werden müssen
Wenn Sie die Erweiterung über eine *MSI-Datei* bereitstellen, müssen Sie **devenv /setup** als Teil Ihrer Installation ausführen, damit Visual Studio Ihre Erweiterungen ermitteln kann.

> [!NOTE]
> Die Informationen in diesem Thema gelten für die Suche nach *devenv.exe* mit Visual Studio 2008 und früher. Informationen zum Ermitteln von *devenv.exe* mit späteren Versionen von Visual Studio finden Sie unter Erkennen von [Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Finden devenv.exe
 Sie können die *devenv.exe-Versionen* jeder [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Version anhand von Registrierungswerten suchen, die Installateure schreiben, indem Sie die RegLocator-Tabelle und die AppSearch-Tabellen verwenden, um die Registrierungswerte als Eigenschaften zu speichern. Weitere Informationen finden Sie unter Erkennen von [Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator-Tabellenzeilen zum Auffinden von devenv.exe aus verschiedenen Versionen von Visual Studio

|Signatur|Root|Schlüssel|Name|type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE-Microsoft-VisualStudio-Datei, 7,0, Setup, VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE-Microsoft-VisualStudio-Datei, 7,1, Setup, VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE-Microsoft-VisualStudio-Datei 8.0-Setup-VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE-Microsoft-VisualStudio-VisualStudio-9.0-Setup-VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch-Tabellenzeilen für entsprechende RegLocator-Tabellenzeilen

|Eigenschaft|Signatur|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Das Visual Studio-Installationsprogramm schreibt z. B. den Registrierungswert **von HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-,9,0-Setup-VS-EnvironmentPath** als *C:-VS2008-Common7-IDE-Devenv.exe*, ein vollständiger Pfad zur ausführbaren Datei, die das Installationsprogramm ausführen muss.

> [!NOTE]
> Da die Spalte Typ der RegLocator-Tabelle 2 ist, ist es nicht erforderlich, zusätzliche Versionsinformationen in der Tabelle Signatur anzugeben.

## <a name="run-devenvexe"></a>Ausführen devenv.exe
 Nachdem die AppSearch-Standardaktion im Installationsprogramm ausgeführt wurde, hat jede Eigenschaft in der AppSearch-Tabelle einen Wert, der auf die Datei *devenv.exe* für die entsprechende Version von Visual Studio verweist. Wenn einer der angegebenen Registrierungswerte nicht vorhanden ist – da diese Version von Visual Studio nicht installiert ist – wird die angegebene Eigenschaft auf null festgelegt.

 Windows Installer unterstützt das Ausführen einer ausführbaren Datei, auf die eine Eigenschaft über den benutzerdefinierten Aktionstyp 50 verweist. Die benutzerdefinierte Aktion sollte die Ausführungsoptionen für `msidbCustomActionTypeInScript` Skripts `msidbCustomActionTypeCommit` (1024) und (512) enthalten, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]um sicherzustellen, dass das VSPackage erfolgreich installiert wurde, bevor es in integriert wurde. Weitere Informationen finden Sie unter [CustomAction-Tabelle](/windows/desktop/msi/customaction-table) und [Optionen für die Ausführung von Benutzerdefinierten Aktionen in Skripten](/windows/desktop/msi/custom-action-in-script-execution-options).

 Benutzerdefinierte Aktionen vom Typ 50 geben die Eigenschaft an, die die ausführbare Datei als Wert der Source-Spalte und Befehlszeilenargumente in der Target-Spalte enthält.

### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction-Tabellenzeilen zum Ausführen von devenv.exe

|Aktion|type|`Source`|Ziel|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Benutzerdefinierte Aktionen müssen in der Tabelle InstallExecuteSequence erstellt werden, um sie für die Ausführung während der Installation zu planen. Verwenden Sie die entsprechende Eigenschaft in jeder Zeile der Spalte Bedingung, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um zu verhindern, dass die benutzerdefinierte Aktion ausgeführt wird, wenn diese Version von nicht auf dem System installiert ist.

> [!NOTE]
> Nullwerteigenschaften werden `False` ausgewertet, wenn sie unter Bedingungen verwendet werden.

 Der Wert der Spalte Sequenz für jede benutzerdefinierte Aktion hängt von anderen Sequenzwerten in Ihrem Windows Installer-Paket ab. Sequenzwerte sollten so sein, dass die benutzerdefinierten Aktionen *von devenv.exe* so nah wie möglich ausgeführt werden, um unmittelbar vor der InstallFinalize-Standardaktion zu arbeiten.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence-Tabelle zum Planen der benutzerdefinierten Aktionen von devenv.exe

|Aktion|Bedingung|Sequenz|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Weitere Informationen
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

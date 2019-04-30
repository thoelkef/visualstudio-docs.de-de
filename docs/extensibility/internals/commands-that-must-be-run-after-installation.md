---
title: Befehle, die nach der Installation ausgeführt werden müssen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76960ae9ffce9cc43510ae1ffd34b8350d58214c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418711"
---
# <a name="commands-that-must-be-run-after-installation"></a>Befehle, die nach der Installation ausgeführt werden muss
Wenn Sie die Erweiterung durch Bereitstellen einer *MSI* -Datei, die Sie ausführen müssen **Devenv/Setup** im Rahmen der Installation in der Reihenfolge für Visual Studio, um Ihre Erweiterungen zu ermitteln.

> [!NOTE]
> Die Informationen in diesem Thema gelten für Suchen *devenv.exe* mit Visual Studio 2008 und früheren Versionen. Informationen zum Ermitteln von *devenv.exe* mit höheren Versionen von Visual Studio finden Sie unter [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Suchen von devenv.exe
 Finden Sie jede Version des *devenv.exe* aus der Registrierung zu Werten, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installationsprogramme schreiben, verwenden die RegLocator-Tabelle und AppSearch Tabellen die Registrierungswerte als Eigenschaften zu speichern. Weitere Informationen finden Sie unter [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Zeilen der RegLocator devenv.exe aus verschiedenen Versionen von Visual Studio zu suchen.

|Signatur|Stammverzeichnis|Key|Name|Typ|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch Tabellenzeilen für die entsprechenden RegLocator Tabellenzeilen

|Eigenschaft|Signatur|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Visual Studio-Installationsprogramm schreibt z. B. des Registrierungswerts von **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** als *C:\VS2008\Common7\IDE\devenv.exe*, einen vollständigen Pfad der ausführbaren Datei, die das Installationsprogramm ausführen muss.

> [!NOTE]
> Da RegLocator Spalte der Tabelle Typ 2 ist, ist es nicht notwendig, die zusätzliche Versionsinformationen in der Signatur anzugeben.

## <a name="run-devenvexe"></a>Ausführen von devenv.exe
 Nach der AppSearch Standardaktionen, die im Installationsprogramm ausgeführt wird, hat jede Eigenschaft in der Tabelle AppSearch einen Wert, der auf die *devenv.exe* -Datei für die entsprechende Version von Visual Studio. Wenn einer der Werte der angegebene Registrierungsschlüssel nicht vorhanden sind, da diese Version von Visual Studio nicht installiert ist – die angegebene Eigenschaft wird festgelegt auf Null.

 Windows Installer unterstützt das Ausführen einer ausführbaren Datei, die auf der eine Eigenschaft verweist über die benutzerdefinierte Aktion geben Sie 50. Die benutzerdefinierte Aktion sollte die Optionen zur Ausführung der im Skript enthalten `msidbCustomActionTypeInScript` (1024) und `msidbCustomActionTypeCommit` (512), um sicherzustellen, dass das VSPackage erfolgreich installiert wurde, bevor Sie die Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [CustomAction-Tabelle](https://docs.microsoft.com/windows/desktop/msi/customaction-table) und [benutzerdefinierte Aktion im Skript Ausführungsoptionen](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options).

 Benutzerdefinierte Aktionen vom Typ 50 Geben Sie die Eigenschaft, die die ausführbare Datei als Wert für die Quellspalte und die Befehlszeilenargumente in der Zielspalte enthält.

### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction Tabellenzeilen devenv.exe ausgeführt.

|Aktion|Typ|Source|Target|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 Benutzerdefinierte Aktionen müssen in die Tabelle InstallExecuteSequence Planung für die Ausführung bei der Installation erstellt werden. Verwenden Sie die entsprechende Eigenschaft in jeder Zeile der Spalte Bedingung, um zu verhindern, dass die benutzerdefinierte Aktion ausgeführt werden, wenn diese Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht auf dem System installiert ist.

> [!NOTE]
> Eigenschaften für NULL-Wert ergeben `False` bei der Verwendung in Bedingungen.

 Der Wert von der Sequence-Spalte für jede benutzerdefinierte Aktion hängt von anderen Sequence-Werte in der Windows Installer-Paket ab. Sequence-Werte muss so, dass die *devenv.exe* benutzerdefinierte Aktionen, die als ausführen wie möglich, um unmittelbar vor der Standardaktion InstallFinalize zu schließen.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence Tabelle so planen Sie die benutzerdefinierten devenv.exe-Aktionen

|Aktion|Bedingung|Sequenz|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Siehe auch
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
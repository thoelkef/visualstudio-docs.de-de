---
title: Befehle, die nach der Installation ausgeführt werden müssen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8448b00085ab7e7a151c935eee4d8a8b1423bd1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961024"
---
# <a name="commands-that-must-be-run-after-installation"></a>Befehle, die nach der Installation ausgeführt werden müssen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie die Erweiterung über eine MSI-Datei bereitstellen, müssen Sie ausführen `devenv /setup` im Rahmen der Installation in der Reihenfolge für Visual Studio, um Ihre Erweiterungen zu ermitteln.  
  
> [!NOTE]
>  Die Informationen in diesem Thema gilt für die DevEnv mit Visual Studio 2008 und früheren Versionen zu suchen. Informationen dazu, wie Sie DevEnv mit höheren Versionen von Visual Studio zu ermitteln, finden Sie unter [Systemanforderungen erkennen](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Suchen von devenv.exe  
 Finden Sie jede Version des devenv.exe aus der Registrierung zu Werten, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installationsprogramme schreiben, mit, dass die RegLocator-Tabelle und die AppSearch Tabelle um die Registrierungswerte als Eigenschaften zu speichern. Weitere Informationen finden Sie unter [Systemanforderungen erkennen](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Zeilen der RegLocator devenv.exe aus verschiedenen Versionen von Visual Studio zu suchen.  
  
|Signature_|Stammverzeichnis|Key|Name|Typ|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch Tabellenzeilen für die entsprechenden RegLocator Tabellenzeilen  
  
|Eigenschaft|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Visual Studio-Installationsprogramm schreibt z. B. des Registrierungswerts von **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** als **C:\VS2008\Common7\IDE\devenv.exe**, einen vollständigen Pfad der ausführbaren Datei, die das Installationsprogramm ausführen muss.  
  
 **Beachten Sie** , da die Spalte RegLocator vom Typ 2 ist, ist es nicht notwendig, die zusätzliche Versionsinformationen in der Signatur anzugeben.  
  
## <a name="running-devenvexe"></a>Ausführen von devenv.exe  
 Nach der AppSearch, die Standardaktion, die im Installationsprogramm ausgeführt wird, hat jede Eigenschaft in der Tabelle AppSearch Wert verweist auf die Datei "devenv.exe" für die entsprechende Version von Visual Studio. Wenn einer der Werte der angegebene Registrierungsschlüssel nicht vorhanden sind, da diese Version von Visual Studio nicht installiert ist – die angegebene Eigenschaft wird festgelegt auf Null.  
  
 Windows Installer unterstützt das Ausführen einer ausführbaren Datei, die auf der eine Eigenschaft verweist über die benutzerdefinierte Aktion geben Sie 50. Die benutzerdefinierte Aktion aufzunehmen, die im Skript Ausführungsoptionen MsidbCustomActionTypeInScript (1024) und MsidbCustomActionTypeCommit (512), um sicherzustellen, dass das VSPackage erfolgreich installiert wurde, bevor Sie die Integration in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter CustomAction-Tabelle und die benutzerdefinierte Aktion im Skript-Ausführungsoptionen.  
  
 Benutzerdefinierte Aktionen vom Typ 50 Geben Sie die Eigenschaft, die die ausführbare Datei als Wert für die Quellspalte und die Befehlszeilenargumente in der Zielspalte enthält.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction Tabellenzeilen devenv.exe ausgeführt.  
  
|Aktion|Typ|Source|Target|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 Benutzerdefinierte Aktionen müssen in die Tabelle InstallExecuteSequence Planung für die Ausführung bei der Installation erstellt werden. Verwenden Sie die entsprechende Eigenschaft in jeder Zeile der Spalte Bedingung, um zu verhindern, dass die benutzerdefinierte Aktion ausgeführt werden, wenn diese Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nicht auf dem System installiert ist.  
  
> [!NOTE]
>  `Null` Auswerten von Eigenschaften zu `False` bei der Verwendung in Bedingungen.  
  
 Der Wert von der Sequence-Spalte für jede benutzerdefinierte Aktion hängt von anderen Sequence-Werte in der Windows Installer-Paket ab. Sequence-Werte muss, dass die benutzerdefinierten devenv.exe-Aktionen, die als Ausführen als möglich, direkt vor dem die Standardaktionen InstallFinalize zu schließen.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence Tabelle so planen Sie die benutzerdefinierten devenv.exe-Aktionen  
  
|Aktion|Bedingung|Sequenz|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

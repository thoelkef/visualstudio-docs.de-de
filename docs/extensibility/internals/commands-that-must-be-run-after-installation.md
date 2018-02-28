---
title: "Befehle, die nach der Installation ausgeführt werden müssen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2ff4b1e572fd1e0c5c500fbd756d01063665bd1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="commands-that-must-be-run-after-installation"></a>Befehle, die nach der Installation ausgeführt werden muss
Wenn Sie die Erweiterung mithilfe einer MSI-Datei bereitstellen, müssen Sie ausführen `devenv /setup` im Rahmen der Installation in der Reihenfolge für Visual Studio, um Ihre Erweiterungen zu ermitteln.  
  
> [!NOTE]
>  Die Informationen in diesem Thema gilt für DevEnv mit Visual Studio 2008 und früheren Versionen zu suchen. Weitere Informationen zum Ermitteln von DevEnv mit höheren Versionen von Visual Studio finden Sie unter [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Suchen von devenv.exe  
 Sie können jede Version finden devenv.exe aus der Registrierung zu Werten, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Installationsprogramme zu schreiben, mit der RegLocator-Tabelle und AppSearch Tabelle zum Speichern der Registrierungswerte als Eigenschaften. Weitere Informationen finden Sie unter [Ermitteln von Systemanforderungen](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator Tabellenzeilen um devenv.exe aus verschiedenen Versionen von Visual Studio zu suchen.  
  
|Signature_|Stamm|Key|name|Typ|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch Tabellenzeilen für die entsprechende RegLocator Tabellenzeilen  
  
|Eigenschaft|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Visual Studio-Installationsprogramm schreibt z. B. den Registrierungswert von **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** als **C:\VS2008\Common7\IDE\devenv.exe**, einen vollständigen Pfad zur ausführbaren Datei muss das Installationsprogramm zu starten.  
  
 **Hinweis** , da die RegLocator Type-Spalte 2 ist, ist es nicht notwendig, die zusätzliche Versionsinformationen in der Signatur Tabelle angeben.  
  
## <a name="running-devenvexe"></a>Devenv.exe ausgeführt  
 Nach der AppSearch Standardaktionen im Installationsprogramm ausgeführt wird, hat jede Eigenschaft in der Tabelle AppSearch einen Wert verweist auf die Datei "devenv.exe" für die entsprechende Version von Visual Studio. Wenn keines der angegebenen Registrierungswerte nicht vorhanden sind, da diese Version von Visual Studio nicht installiert ist – die angegebene Eigenschaft festgelegt ist auf Null.  
  
 Windows Installer-unterstützt, die Ausführung einer ausführbaren Datei, die auf der eine Eigenschaft zeigt über die benutzerdefinierte Aktion 50 eingeben. Die benutzerdefinierte Aktion aufzunehmen, die im Skript Ausführungsoptionen MsidbCustomActionTypeInScript (1024) und MsidbCustomActionTypeCommit (512), um sicherzustellen, dass das VSPackage erfolgreich installiert wurde, vor der Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter CustomAction-Tabelle und die benutzerdefinierte Aktion im Skript Ausführungsoptionen.  
  
 Benutzerdefinierte Aktionen vom Typ 50 Geben Sie die Eigenschaft, die die ausführbare Datei als Wert für die Quellspalte und die Befehlszeilenargumente in der Zielspalte enthält.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction Tabellenzeilen devenv.exe ausgeführt.  
  
|Aktion|Typ|Quelle|Ziel|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/ Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/ Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/ Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/ Setup|  
  
 Benutzerdefinierte Aktionen müssen in die Tabelle InstallExecuteSequence so planen Sie sie für die Ausführung bei der Installation erstellt werden. Verwenden Sie die entsprechende Eigenschaft in jeder Zeile der Spalte Bedingung, um zu verhindern, dass die benutzerdefinierte Aktion ausgeführt werden, wenn diese Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist nicht auf dem System installiert.  
  
> [!NOTE]
>  `Null`Eigenschaften, die zum Auswerten `False` bei der Verwendung in Bedingungen.  
  
 Der Wert der Sequence-Spalte für jede benutzerdefinierte Aktion hängt von anderen Sequence-Werte in der Windows Installer-Paket. Sequenzwerte sollte sein, sodass die ausführende devenv.exe für benutzerdefinierte Aktionen als möglich, direkt vor dem die Standardaktionen InstallFinalize schließen.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence Tabelle so planen Sie die benutzerdefinierten devenv.exe-Aktionen  
  
|Aktion|Bedingung|Sequenz|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
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
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841233"
---
# <a name="commands-that-must-be-run-after-installation"></a>Befehle, die nach der Installation ausgeführt werden müssen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie die Erweiterung über eine MSI-Datei bereitstellen, müssen Sie `devenv /setup` als Teil der Installation ausführen, damit Visual Studio Ihre Erweiterungen ermitteln kann.  
  
> [!NOTE]
> Die Informationen in diesem Thema gelten für die Suche nach devenv mit Visual Studio 2008 und früher. Informationen dazu, wie Sie devenv mit neueren Versionen von Visual Studio ermitteln, finden Sie unter [Ermitteln der System Anforderungen](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Suchen nach devenv.exe  
 Sie können die devenv.exe einer Version aus Registrierungs Werten suchen, die von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installationsprogrammen geschrieben werden. verwenden Sie dazu die reglocator-Tabelle und die AppSearch-Tabelle, um die Registrierungs Werte als Eigenschaften zu speichern. Weitere Informationen finden Sie unter [Ermitteln der System Anforderungen](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Relocator-Tabellenzeilen, um devenv.exe aus verschiedenen Versionen von Visual Studio zu suchen  
  
|Signature_|Root|Schlüssel|Name|type|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|Software\microsoft\visualstudio\7.0\setup\vs|Umgebungs Pfad|2|  
|RL_DevenvExe_2003|2|Software\microsoft\visualstudio\7,1 \setup\vs|Umgebungs Pfad|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\setup\vs|Umgebungs Pfad|2|  
|RL_DevenvExe_2008|2|Software\Microsoft\VisualStudio\9.0\setup\vs|Umgebungs Pfad|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Hiermit werden Tabellenzeilen für entsprechende reglocator-Tabellenzeilen durchsucht.  
  
|Eigenschaft|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Der Visual Studio-Installer schreibt z. b. den Registrierungs Wert **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\umgebungspfad** in **C:\VS2008\Common7\IDE\devenv.exe**, einen kompletten Pfad zu der ausführbaren Datei, die vom Installationsprogramm ausgeführt werden muss.  
  
 **Hinweis** Da die reglocator-Typspalte 2 ist, ist es nicht erforderlich, zusätzliche Versionsinformationen in der Signatur Tabelle anzugeben.  
  
## <a name="running-devenvexe"></a>Ausführen devenv.exe  
 Nachdem die AppSearch-Standardaktion im Installationsprogramm ausgeführt wurde, weist jede Eigenschaft in der AppSearch-Tabelle einen Wert auf, der auf die devenv.exe Datei für die zugehörige Version von Visual Studio zeigt. Wenn einer der angegebenen Registrierungs Werte nicht vorhanden ist – da diese Version von Visual Studio nicht installiert ist – wird die angegebene Eigenschaft auf NULL festgelegt.  
  
 Windows Installer unterstützt das Ausführen einer ausführbaren Datei, auf die eine Eigenschaft durch den benutzerdefinierten Aktionstyp 50 zeigt. Die benutzerdefinierte Aktion sollte die in-Script-Ausführungs Optionen, msidbcustomaction typeinscript (1024) und msidbcustomaction typecommit (512) enthalten, um sicherzustellen, dass das VSPackage erfolgreich installiert wurde, bevor es in integriert wird [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter CustomAction Table und Custom Action in-Script Execution Options.  
  
 Benutzerdefinierte Aktionen des Typs 50 geben die Eigenschaft an, die die ausführbare Datei als Wert der Quell Spalte und Befehlszeilenargumente in der Ziel Spalte enthält.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Zu testbare CustomAction-Tabellenzeilen devenv.exe  
  
|Aktion|type|`Source`|Ziel|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Benutzerdefinierte Aktionen müssen in der InstallExecuteSequence-Tabelle erstellt werden, um die Ausführung während der Installation zu planen. Verwenden Sie die entsprechende-Eigenschaft in jeder Zeile der Spalte Bedingung, um zu verhindern, dass die benutzerdefinierte Aktion ausgeführt wird, wenn diese Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nicht auf dem System installiert ist.  
  
> [!NOTE]
> `Null` Eigenschaften `False` werden als ausgewertet, wenn Sie in Bedingungen verwendet werden.  
  
 Der Wert der Sequence-Spalte für jede benutzerdefinierte Aktion hängt von anderen Sequenz Werten im Windows Installer Paket ab. Die Sequenzwerte sollten so lauten, dass die devenv.exe benutzerdefinierten Aktionen so nah wie möglich ausgeführt werden, unmittelbar vor der Standardaktion InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>InstallExecuteSequence-Tabelle, um die devenv.exe benutzerdefinierten Aktionen zu planen  
  
|Aktion|Bedingung|Sequenz|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

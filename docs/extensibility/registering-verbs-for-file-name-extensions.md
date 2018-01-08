---
title: "Registrieren von Verben für Dateinamenerweiterungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ff1902689524dd980c8223ca83863238254df448
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="registering-verbs-for-file-name-extensions"></a>Registrieren von Verben für Dateinamenerweiterungen
Die Zuordnung der Dateinamenerweiterung mit einer Anwendung wurde in der Regel eine bevorzugte Maßnahme, das auftritt, wenn ein Benutzer eine Datei doppelklickt. Dies bevorzugte ein Verb, z. B. open Aktion verknüpft ist, die der Aktion entspricht.  
  
 Sie können die Verben, die ein Programmbezeichner (ProgID) für eine Erweiterung zugeordnet sind, mithilfe des Befehlsshell Schlüssels befindet sich am HKEY_CLASSES_ROOT registrieren\\*progid*\shell. Weitere Informationen finden Sie unter [Dateitypen](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Registrieren von Standardverben  
 Das Betriebssystem erkennt die folgenden Standardverben:  
  
-   Öffnen  
  
-   Bearbeiten  
  
-   Wiedergabe  
  
-   Print  
  
-   Vorschau  
  
 Registrieren Sie nach Möglichkeit einem Standardverb. Häufigste Auswahl wird das Verb "Open". Verwenden Sie das Bearbeiten-Verb, nur, wenn Sie ein klaren Unterschied zwischen dem Öffnen der Datei, und bearbeiten die Datei vorhanden ist. Beispielsweise wird eine HTM-Datei öffnen im Browser, während der Bearbeitung einer HTM-Datei einen HTML-Editor wird gestartet. Standardverben sind mit dem Gebietsschema des Betriebssystems lokalisiert.  
  
> [!NOTE]
>  Legen Sie beim Registrieren von Standardverben nicht den Standardwert für den Schlüssel geöffnet. Der Standardwert enthält die Anzeigezeichenfolge im Menü auf. Das Betriebssystem stellt diese Zeichenfolge für Standardverben bereit.  
  
 Projektdateien registriert werden soll, um eine neue Instanz der starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] beim Öffnen der das. Das folgende Beispiel veranschaulicht eine Standardverb-Registrierung für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Projekt.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Öffnen eine Datei in eine vorhandene Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], registrieren Sie einen DDEEXEC-Schlüssel. Das folgende Beispiel veranschaulicht eine Standardverb-Registrierung für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] cs-Datei.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>Die Standardaktion festlegen  
 Das Standard-Verb ist die Aktion, die ausgeführt wird, wenn ein Benutzer eine Datei im Windows Explorer doppelklickt. Das Standard-Verb ist das Verb, das als Standardwert für den HKEY_CLASSES_ROOT angegebene\\*progid*\Shell Schlüssel. Wenn kein Wert angegeben ist, wird das Standard-Verb der erste in der HKEY_CLASSES_ROOT das angegebene Verb\\*progid*\Shell Schlüsselliste.  
  
> [!NOTE]
>  Wenn Sie beabsichtigen, das Standard-Verb für eine Erweiterung in eine Seite-an-Seite-Bereitstellung zu ändern, sollten Sie die Auswirkungen auf die Installation und Deinstallation. Während der Installation wird der ursprüngliche Standardwert überschrieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von parallelen Dateizuordnungen](../extensibility/managing-side-by-side-file-associations.md)
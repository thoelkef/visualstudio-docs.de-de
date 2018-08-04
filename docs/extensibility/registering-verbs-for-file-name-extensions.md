---
title: Registrieren von Verben für Dateierweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8004176fb64244aecde276226683a53c013d3b31
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513132"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Registrieren von Verben für Dateierweiterungen
Die Zuordnung der Erweiterung zu einer Anwendung hat normalerweise eine bevorzugte Maßnahme, die auftritt, wenn ein Benutzer eine Datei doppelklickt. Dies wird bevorzugt, dass die Aktion mit einem Verb, z. B. geöffnet ist, verknüpft ist, die die Aktion entspricht.  
  
 Sie können die Verben, die ein Programmbezeichner (ProgID) für eine Erweiterung zugeordnet sind, mit der Shell-Schlüssel befindet sich unter HKEY_CLASSES_ROOT registrieren\\*progid*\shell. Weitere Informationen finden Sie unter [Dateitypen](/windows/desktop/shell/fa-file-types).  
  
## <a name="registering-standard-verbs"></a>Registrieren von Standard-Verben  
 Das Betriebssystem erkennt die folgenden standard-Verben:  
  
-   Öffnen  
  
-   Bearbeiten  
  
-   Wiedergabe  
  
-   Print  
  
-   Vorschau  
  
 Wann immer möglich, registrieren Sie ein standard-Verb. Die Wahl üblicherweise ist das Open-Verb. Verwenden Sie das Edit-Verb, nur, wenn Sie ein klaren Unterschied zwischen dem Öffnen der Datei, und Bearbeiten der Datei vorhanden ist. Beispielsweise wird eine HTM-Datei öffnen im Browser während der Bearbeitung einer HTM-Datei einen HTML-Editor wird gestartet. Standard-Verben sind mit dem Gebietsschema des Betriebssystems lokalisiert.  
  
> [!NOTE]
>  Wenn Standardverben registrieren zu können, der Standardwert für den geöffneten Schlüssel nicht festgelegt werden. Standardmäßig ist der Wert enthält die Zeichenfolge für die Sie im Menü. Das Betriebssystem stellt diese Zeichenfolge für Standardverben bereit.  
  
 Projektdateien registriert werden soll, um eine neue Instanz der starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Wenn ein Benutzer öffnet die Datei. Das folgende Beispiel veranschaulicht eine standard-Verb-Registrierung für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Projekt.  
  
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
  
 Zum Öffnen einer Datei in eine vorhandene Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], registrieren Sie einen Schlüssel DDEEXEC. Das folgende Beispiel veranschaulicht eine standard-Verb-Registrierung für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] cs-Datei.  
  
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
  
## <a name="setting-the-default-verb"></a>Das Standard-Verb festlegen  
 Das Standard-Verb ist die Aktion, die ausgeführt wird, wenn ein Benutzer eine Datei in Windows Explorer doppelklickt. Das Standard-Verb ist das Verb, die als Standardwert für den HKEY_CLASSES_ROOT angegebene\\*progid*\Shell Schlüssel. Wenn kein Wert angegeben ist, wird das Standardverb das erste Verb in der HKEY_CLASSES_ROOT angegebenen\\*progid*\Shell Schlüsselliste.  
  
> [!NOTE]
>  Wenn Sie das Standard-Verb für eine Erweiterung in einer Bereitstellung für die Seite-an-Seite ändern möchten, sollten Sie die Auswirkungen auf die Installation und Deinstallation. Während der Installation wird der ursprüngliche Standardwert überschrieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von parallelen Dateizuordnungen](../extensibility/managing-side-by-side-file-associations.md)
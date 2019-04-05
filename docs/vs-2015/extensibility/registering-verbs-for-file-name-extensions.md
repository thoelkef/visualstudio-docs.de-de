---
title: Registrieren von Verben für Dateierweiterungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ff021643313d267cc92d2f08afa8f41a3ce806b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961735"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Registrieren von Verben für Dateierweiterungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Zuordnung der Erweiterung zu einer Anwendung hat normalerweise eine bevorzugte Maßnahme, die auftritt, wenn ein Benutzer eine Datei doppelklickt. Dies wird bevorzugt, dass die Aktion mit einem Verb, z. B. geöffnet ist, verknüpft ist, die die Aktion entspricht.  
  
 Sie können die Verben, die ein Programmbezeichner (ProgID) für eine Erweiterung zugeordnet sind, mit der Shell-Schlüssel befindet sich unter HKEY_CLASSES_ROOT registrieren\\*progid*\shell. Weitere Informationen finden Sie unter [Dateitypen](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Registrieren von Standard-Verben  
 Das Betriebssystem erkennt die folgenden standard-Verben:  
  
- Öffnen  
  
- Bearbeiten  
  
- Wiedergabe  
  
- Print  
  
- Vorschau  
  
  Wann immer möglich, registrieren Sie ein standard-Verb. Die Wahl üblicherweise ist das Open-Verb. Verwenden Sie das Edit-Verb, nur, wenn Sie ein klaren Unterschied zwischen dem Öffnen der Datei, und Bearbeiten der Datei vorhanden ist. Beispielsweise wird eine HTM-Datei öffnen im Browser während der Bearbeitung einer HTM-Datei einen HTML-Editor wird gestartet. Standard-Verben sind mit dem Gebietsschema des Betriebssystems lokalisiert.  
  
> [!NOTE]
>  Wenn Standardverben registrieren zu können, der Standardwert für den geöffneten Schlüssel nicht festgelegt werden. Standardmäßig ist der Wert enthält die Zeichenfolge für die Sie im Menü. Das Betriebssystem stellt diese Zeichenfolge für Standardverben bereit.  
  
 Projektdateien registriert werden soll, um eine neue Instanz der starten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Wenn ein Benutzer öffnet die Datei. Das folgende Beispiel veranschaulicht eine standard-Verb-Registrierung für ein [!INCLUDE[csprcs](../includes/csprcs-md.md)] Projekt.  
  
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
  
 Zum Öffnen einer Datei in eine vorhandene Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], registrieren Sie einen Schlüssel DDEEXEC. Das folgende Beispiel veranschaulicht eine standard-Verb-Registrierung für ein [!INCLUDE[csprcs](../includes/csprcs-md.md)] cs-Datei.  
  
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

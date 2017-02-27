---
title: "Registrieren von Verben f&#252;r Dateinamenerweiterungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Registrieren von Verben"
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Registrieren von Verben f&#252;r Dateinamenerweiterungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Zuordnung der Erweiterung mit einer Anwendung hat im Allgemeinen eine gewünschte Aktion, die bei einem Doppelklick auf eine Datei. Das bevorzugte Aktion mit einem Verb, z. B. open, verknüpft ist, die der Aktion entspricht.  
  
 Registrieren Sie Verben, die eine programmgesteuerte Bezeichner \(ProgID\) für eine Erweiterung zugeordnet sind, mithilfe der Befehlsshell diesen Schlüssel auf HKEY\_CLASSES\_ROOT\\*progid*\\shell. Weitere Informationen finden Sie unter [Dateitypen](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## Registrieren von Standardverben  
 Das Betriebssystem erkennt die folgenden Standardverben:  
  
-   Öffnen  
  
-   Bearbeiten  
  
-   Wiedergabe  
  
-   Print  
  
-   Vorschau  
  
 Wann immer möglich, registrieren Sie ein standard\-Verb. Am häufigsten wird das Verb "Open". Verwenden Sie das Bearbeiten\-Verb, nur dann, wenn ein klaren Unterschied zwischen öffnen und Bearbeiten der Datei. Beispielsweise wird eine HTM\-Datei öffnen im Browser während der Bearbeitung einer HTM\-Datei einen HTML\-Editor wird gestartet. Standardverben sind mit dem Operating Systemgebietsschema lokalisiert.  
  
> [!NOTE]
>  Legen Sie beim Registrieren von Standardverben nicht der Standardwert für den Schlüssel geöffnet. Standardmäßig enthält die Zeichenfolge im Menü. Das Betriebssystem stellt diese Zeichenfolge für Standardverben bereit.  
  
 Projektdateien registriert werden soll, um eine neue Instanz der starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] beim Öffnen der das. Das folgende Beispiel veranschaulicht eine standard\-Verb\-Registrierung für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Projekt.  
  
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
  
 Zum Öffnen einer Datei in eine vorhandene Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], einen DDEEXEC\-Schlüssel zu registrieren. Das folgende Beispiel veranschaulicht eine standard\-Verb\-Registrierung für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] cs\-Datei.  
  
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
  
## Die Standardaktion festlegen  
 Das Standard\-Verb ist die Aktion, die ausgeführt wird, wenn ein Benutzer eine Datei in Windows Explorer doppelklickt. Die Standardaktion ist das Verb, das als Standardwert für die HKEY\_CLASSES\_ROOT\\ angegebene*progid*\\Shell\-Schlüssel. Wenn kein Wert angegeben wird, ist das Standard\-Verb das erste Verb in der HKEY\_CLASSES\_ROOT\\ angegebenen*progid*\\Shell Schlüsselliste.  
  
> [!NOTE]
>  Wenn Sie das Standard\-Verb für eine Erweiterung in einer Seite\-an\-Seite\-Bereitstellung ändern möchten, sollten Sie die Auswirkung auf die Installation und Deinstallation. Während der Installation wird der ursprüngliche Standardwert überschrieben.  
  
## Siehe auch  
 [Creating a File Association](_win32_file_associations)   
 [Verwalten von Dateizuordnungen Side\-by\-Side](../extensibility/managing-side-by-side-file-associations.md)
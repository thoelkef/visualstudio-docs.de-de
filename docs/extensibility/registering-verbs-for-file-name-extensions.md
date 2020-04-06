---
title: Registrieren von Verben für Dateinamenerweiterungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701533"
---
# <a name="register-verbs-for-file-name-extensions"></a>Register verbs für Dateinamenerweiterungen
Die Zuordnung einer Dateinamenerweiterung mit einer Anwendung weist im Allgemeinen eine bevorzugte Aktion auf, die auftritt, wenn ein Benutzer auf eine Datei doppelklickt. Diese bevorzugte Aktion ist mit einem Verb verknüpft, z. B. offen, das der Aktion entspricht.

 Sie können Verben, die einem programmgesteuerten Bezeichner (ProgID) zugeordnet sind, für eine Erweiterung registrieren, indem Sie den Shell-Schlüssel verwenden, der sich unter **HKEY_CLASSES_ROOT\{progid-shell**befindet. Weitere Informationen finden Sie unter [Dateitypen](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Standardverben registrieren
 Das Betriebssystem erkennt die folgenden Standardverben:

- Öffnen

- Edit (Bearbeiten)

- Abspielen

- print

- Vorschau

  Registrieren Sie nach Möglichkeit ein Standardverb. Die häufigste Wahl ist das Open Verb. Verwenden Sie das Verb Bearbeiten nur, wenn es einen klaren Unterschied zwischen dem Öffnen der Datei und dem Bearbeiten der Datei gibt. Wenn Sie z. B. eine *HTM-Datei* öffnen, wird sie im Browser angezeigt, während durch bearbeiten einer *HTM-Datei* ein HTML-Editor gestartet wird. Standardverben werden mit dem Betriebssystemgebietsschema lokalisiert.

> [!NOTE]
> Legen Sie beim Registrieren von Standardverben nicht den Standardwert für den Open-Schlüssel fest. Der Standardwert enthält die Anzeigezeichenfolge im Menü. Das Betriebssystem stellt diese Zeichenfolge für Standardverben zur Verfügung.

 Projektdateien sollten registriert werden, um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine neue Instanz zu starten, wenn ein Benutzer die Datei öffnet. Das folgende Beispiel veranschaulicht eine Standardverbregistrierung für ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Projekt.

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

 Um eine Datei in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]vorhandenen Instanz von zu öffnen, registrieren Sie einen DDEEXEC-Schlüssel. Das folgende Beispiel veranschaulicht eine Standardverbregistrierung für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs-Datei.*

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

## <a name="set-the-default-verb"></a>Festlegen des Standardverbs
 Das Standardverb ist die Aktion, die ausgeführt wird, wenn ein Benutzer im Windows Explorer auf eine Datei doppelklickt. Das Standardverb ist das Verb, das als Standardwert für den **HKEY_CLASSES_ROOT\\*progid-Shell-Taste*** angegeben ist. Wenn kein Wert angegeben ist, ist das Standardverb das erste Verb, das in der **HKEY_CLASSES_ROOT\\progid-Shell-Schlüsselliste*progid*** angegeben ist.

> [!NOTE]
> Wenn Sie das Standardverb für eine Erweiterung in einer Side-by-Side-Bereitstellung ändern möchten, sollten Sie die Auswirkungen auf die Installation und Entfernung berücksichtigen. Während der Installation wird der ursprüngliche Standardwert überschrieben.

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von seitenebenigen Dateizuordnungen](../extensibility/managing-side-by-side-file-associations.md)

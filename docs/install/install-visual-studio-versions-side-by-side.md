---
title: Parallele Installation mehrerer Visual Studio-Versionen
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: 428c41a96de90494167d04ded8722d49c76afc71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114646"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Parallele Installation mehrerer Visual Studio-Versionen

Sie können Visual Studio auf einem Computer installieren, auf dem bereits eine frühere oder spätere Version von Visual Studio installiert ist.

::: moniker range="vs-2017"

Bevor Sie Versionen parallel installieren, sollten Sie sich mit folgenden Bedingungen vertraut machen:

* Wenn Sie Visual Studio 2017 verwenden, um eine Projektmappe zu öffnen, die in Visual Studio 2015 erstellt wurde, können Sie die Projektmappe später erneut in der früheren Version öffnen und ändern, sofern Sie keine Funktionen implementiert haben, die für Visual Studio 2017 spezifisch sind.

* Wenn Sie versuchen, eine Projektmappe mit Visual Studio 2017 zu öffnen, die mit Visual Studio 2015 oder einer früheren Version erstellt wurde, müssen Sie möglicherweise Ihre Projekte und Dateien ändern, damit diese mit Visual Studio 2017 kompatibel sind. Weitere Informationen finden Sie unter [Projektmigration und Upgradereferenz für Visual Studio 2017](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017).

::: moniker-end

::: moniker range=">= vs-2019"

Bevor Sie Versionen parallel installieren, sollten Sie sich mit folgenden Bedingungen vertraut machen:

* Wenn Sie Visual Studio 2019 verwenden, um eine Projektmappe zu öffnen, die in Visual Studio 2017 erstellt wurde, können Sie die Projektmappe später erneut in der früheren Version öffnen und ändern, sofern Sie keine Funktionen implementiert haben, die für Visual Studio 2019 spezifisch sind.

* Wenn Sie versuchen, eine Projektmappe mit Visual Studio 2019 zu öffnen, die mit Visual Studio 2017 oder einer früheren Version erstellt wurde, müssen Sie möglicherweise Ihre Projekte und Dateien ändern, damit diese mit Visual Studio 2019 kompatibel sind. Weitere Informationen finden Sie unter [Projektmigration und Upgradereferenz für Visual Studio 2017](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* Wenn Sie eine Visual Studio-Version auf einem Computer deinstallieren, auf dem mehrere Versionen installiert sind, werden die Visual Studio-Dateizuordnungen für alle Versionen entfernt.

* Visual Studio aktualisiert die Erweiterungen nicht automatisch, da nicht alle Erweiterungen kompatibel sind. Installieren Sie erneut die Erweiterungen aus dem [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oder vom Softwareherausgeber.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework-Versionen und parallele Installationen

Visual Basic-, Visual C#- und Visual F#-Projekte nutzen die Option **Zielframework** im **Projekt-Designer**, um festzulegen, welche Version des .NET Frameworks ein Projekt verwendet. Für ein C++-Projekt können Sie das Zielframework durch Bearbeiten der Projektdatei (.vcxproj) ändern. Weitere Informationen finden Sie unter [Kompatibilität von .NET Framework-Versionen](/dotnet/framework/migration-guide/version-compatibility).

Wenn Sie ein Projekt erstellen, können Sie angeben, auf welche Version von .NET Framework das Projekt in der Liste **.NET Framework** im Dialogfeld **Neues Projekt** abzielt.

Sprachspezifische Informationen finden Sie im entsprechenden Thema in der folgenden Tabelle.

::: moniker range="vs-2017"

| Sprache | Thema |
|--------------|-----------|
| Visual Basic | [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Entwickeln mit Visual F# in Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/). |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md?view=vs-2017)
* [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Sprache | Thema |
|--------------|-----------|
| Visual Basic | [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Entwickeln mit Visual F# in Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/). |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

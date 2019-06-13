---
title: Gezielte .NET Framework-Versionen
ms.date: 02/06/2018
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cb7af190ac7fc5d4d5ce547029689f6c902a6e4f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747617"
---
# <a name="framework-targeting-overview"></a>Übersicht über .NET Framework

In Visual Studio können Sie die Version von .NET angeben, dass Ihr Projekt verwendet werden soll. Für .NET Framework-apps auf einem anderen Computer, die Framework-Version ausgeführt wird, die die Anwendung ausgerichtet ist mit der Frameworkversion kompatibel sein müssen, die auf dem Computer installiert ist.

Weitere Informationen zu Zielframeworks, finden Sie unter [Zielframeworks](/dotnet/standard/frameworks).

Sie können auch eine Projektmappe erstellen, die Projekte enthält, die verschiedene Versionen von .NET abzielen. Durch frameworkziele wird gewährleistet, dass die Anwendung nur die Funktionen verwendet, die in der angegebenen Frameworkversion verfügbar ist.

> [!TIP]
> Sie können auch Anwendungen für unterschiedliche Plattformen als Ziel verwenden. Weitere Informationen finden Sie unter [Multitargeting](../msbuild/msbuild-multitargeting-overview.md) (Festlegen von Zielversionen).

## <a name="framework-targeting-features"></a>Frameworkzielfunktionen

Frameworkziele umfassen folgende Funktionen:

- Wenn Sie ein Projekt, der eine früheren Framework-Version abzielt öffnen, Visual Studio können automatisch aktualisieren Sie das Projekt oder lassen Sie das Ziel als-ist.

- Wenn Sie ein Projekt .NET Framework erstellen, können Sie die Version von .NET Framework angeben, die Sie abzielen möchten.

- Sie können [mehrere Zielframeworks](/dotnet/standard/frameworks#how-to-specify-target-frameworks) in einem einzelnen Projekt.

- Sie können eine andere Version von .NET in unterschiedliche Projekte in der gleichen Projektmappe abzielen.

- Sie können die Version von .NET, mit der ein vorhandenes Projekt ändern Ziele.

   Wenn Sie ändern die Version von .NET, ein Projekt ausgerichtet ist, Visual Studio mit der erforderlichen, Änderungen an verweisen und Konfigurationsdateien.

Wenn Sie sich an einem Projekt arbeiten, der eine früheren Framework-Version, Visual Studio dynamisch ausgerichtet ist, ändert die Entwicklungsumgebung wie folgt:

- Filtern von Elementen in den Dialogfeldern **Neues Element hinzufügen**, **Neuen Verweis hinzufügen** und **Dienstverweis hinzufügen**, um die Optionen auszulassen, die in der Zielversion nicht verfügbar sind.

- Filtern von benutzerdefinierten Steuerelementen in der **Toolbox**, um die Steuerelemente zu entfernen, die in der Zielversion nicht verfügbar sind, und um nur die neuesten Steuerelemente anzuzeigen, wenn mehrere Steuerelemente für die Zielversion verfügbar sind.

- Filtern von **IntelliSense** um Sprachfunktionen auszulassen, die in der Zielversion nicht verfügbar sind.

- Filtern von Eigenschaften in der **Eigenschaften** Fenster aus, um diejenigen auslassen, die in der Zielversion nicht verfügbar sind.

- Filtern von Menüoptionen, um Optionen auszulassen, die in der Zielversion nicht verfügbar sind.

- Für Builds werden die Version des Compilers und die Compileroptionen verwendet, die für die Zielversion geeignet sind.

> [!NOTE]
> - Durch Frameworkziele wird nicht garantiert, dass die Anwendung ordnungsgemäß ausgeführt wird. Sie müssen die Anwendung dennoch testen, um sicherzustellen, dass Sie mit der Zielversion ausgeführt wird.
> - Sie können keine Frameworkversionen unter .NET Framework 2.0 abzielen.

## <a name="select-a-target-framework-version"></a>Auswählen einer Zielframeworkversion

Wenn Sie ein Projekt .NET Framework erstellen, können Sie die .NET Framework-Version auswählen, nach der Auswahl einer Projektvorlage. Die Liste der verfügbaren Frameworks enthält die installierten Framework-Versionen, die auf den Typ der ausgewählten Vorlage anwendbar sind. Für .NET Framework - Projektvorlagen, z. B. .NET Core-Vorlagen, die **Framework** Dropdown-Liste nicht angezeigt wird.

::: moniker range="vs-2017"

![Framework-Dropdownliste in VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Framework-Dropdownliste in VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

In einem vorhandenen Projekt können Sie die Zielversion von .NET in das Dialogfeld für die Eigenschaften des Projekts ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Eine Version von .NET als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Auflösen von System- und Benutzerassemblyverweisen

Um eine Version von .NET als Ziel festzulegen, müssen Sie zunächst die entsprechenden Assemblyverweise installieren. Sie können Developer Packs für verschiedene Versionen von .NET auf den [.NET – downloads](https://www.microsoft.com/net/download/windows) Seite.

Für .NET Framework-Projekten die **Verweis hinzufügen** Dialogfeld deaktiviert-Systemassemblys, die für .NET Framework-Zielversion nicht relevant, damit sie nicht versehentlich zu einem Projekt hinzugefügt werden können. (Systemassemblys sind *DLL*-Dateien, die in einer .NET Framework-Version enthalten sind.) Verweise, die auf eine Frameworkversion gehören, der höher als die Zielversion werden nicht aufgelöst und Steuerelemente, die einem solchen Verweis abhängen, können nicht hinzugefügt werden. Wenn Sie einen solchen Verweis aktivieren möchten, setzen Sie das .NET Framework-Ziel des Projekts auf eine Version zurück, die den Verweis enthält. Weitere Informationen finden Sie unter [Vorgehensweise: Frameworkversion als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Weitere Informationen zu Assemblyverweisen finden Sie unter [Auflösen von Assemblys zur Entwurfszeit](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Aktivieren von LINQ

Wenn Sie .NET Framework 3.5 oder eine höhere Version als Ziel verwenden, werden automatisch ein Verweis auf **System.Core** und ein Import auf Projektebene für <xref:System.Linq> (nur in Visual Basic) hinzugefügt. Wenn Sie LINQ-Features verwenden möchten, müssen Sie zusätzlich `Option Infer` aktivieren (nur in Visual Basic). Der Verweis und der Import werden automatisch entfernt, wenn Sie die Zielversion auf eine frühere .NET Framework-Version ändern. Weitere Informationen finden Sie unter [Arbeiten mit LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Siehe auch

- [Zielframeworks](/dotnet/standard/frameworks)
- [Projekte für mehrere Zielframeworkversionen (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Vorgehensweise: How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
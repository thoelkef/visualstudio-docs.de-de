---
title: Festlegen von .NET Framework als Ziel.
ms.date: 02/06/2018
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 451464cd2576c1dd70c7b8235cead327b2f05ca2
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355272"
---
# <a name="visual-studio-multi-targeting-overview"></a>Übersicht: Ausrichtung auf mehrere Zielframeworkversionen in Visual Studio

In Visual Studio können Sie die Version oder das Profil von .NET Framework angeben, auf die bzw. das Sie das Projekt ausrichten möchten. Damit eine Anwendung auf einem anderen Computer ausgeführt werden kann, muss die Version von .NET Framework, auf die die Anwendung ausgerichtet ist, mit der Version von .NET Framework, die auf dem Computer installiert ist, kompatibel sein.

Sie können auch eine Projektmappe mit Projekten erstellen, die auf andere Versionen des Frameworks ausgerichtet sind. Durch Frameworkziele wird gewährleistet, dass die Anwendung nur die Funktionalität verwendet, die in der angegebenen Version des Frameworks verfügbar ist.

> [!TIP]
> Sie können auch Anwendungen für unterschiedliche Plattformen als Ziel verwenden. Weitere Informationen finden Sie unter [Multitargeting](../msbuild/msbuild-multitargeting-overview.md) (Festlegen von Zielversionen).

## <a name="framework-targeting-features"></a>Frameworkzielfunktionen

Frameworkziele umfassen folgende Funktionen:

- Wenn Sie ein Projekt öffnen, das auf eine frühere Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ausgerichtet ist, kann Visual Studio das Projekt automatisch aktualisieren oder die Zielversion unverändert lassen.

- Wenn Sie ein Projekt erstellen, können Sie die gewünschte .NET Framework-Zielversion angeben.

- Sie können die Version von .NET Framework ändern, auf die ein vorhandenes Projekt abzielt.

- Sie können eine andere .NET Framework-Version als Zielversion für unterschiedliche Projekte in der gleichen Projektmappe festlegen.

- Wenn Sie die Version von .NET Framework ändern, auf die ein Projekt ausgerichtet ist, werden in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] alle erforderlichen Änderungen an Verweisen und Konfigurationsdateien vorgenommen.

Visual Studio kann dynamisch Änderungen in der Entwicklungsumgebung vornehmen, wenn Sie mit einem Projekt arbeiten, das eine frühere [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Version als Ziel hat. Dazu zählen u. a. folgende Aktionen:

- Filtern von Elementen in den Dialogfeldern **Neues Element hinzufügen**, **Neuen Verweis hinzufügen** und **Dienstverweis hinzufügen**, um die Optionen auszulassen, die in der Zielversion nicht verfügbar sind.

- Filtern von benutzerdefinierten Steuerelementen in der **Toolbox**, um die Steuerelemente zu entfernen, die in der Zielversion nicht verfügbar sind, und um nur die neuesten Steuerelemente anzuzeigen, wenn mehrere Steuerelemente für die Zielversion verfügbar sind.

- Filtern von **IntelliSense**, um Sprachfeatures auszulassen, die in der Zielversion nicht verfügbar sind.

- Filtern von Eigenschaften im Fenster **Eigenschaften**, um die Eigenschaften auszulassen, die in der Zielversion nicht verfügbar sind.

- Filtern von Menüoptionen, um Optionen auszulassen, die in der Zielversion nicht verfügbar sind.

- Für Builds werden die Version des Compilers und die Compileroptionen verwendet, die für die Zielversion geeignet sind.

> [!NOTE]
> Durch Frameworkziele wird nicht garantiert, dass die Anwendung ordnungsgemäß ausgeführt wird. Sie müssen die Anwendung dennoch testen, um sicherzustellen, dass Sie mit der Zielversion ausgeführt wird. Sie können keine Frameworkversionen als Ziel verwenden, die älter als .NET Framework 2.0 sind.

## <a name="select-a-target-framework-version"></a>Auswählen einer Zielframeworkversion

Wenn Sie ein Projekt erstellen, wählen Sie die .NET Framework-Zielversion nach dem Auswählen einer Projektvorlage aus. Die Liste der verfügbaren Frameworks enthält die installierten Framework-Versionen, die auf den Typ der ausgewählten Vorlage anwendbar sind. Für Vorlagentypen, die .NET Framework nicht benötigen, z.B. .NET Core-Vorlagen, wird die **Framework**-Dropdownliste ausgeblendet.

::: moniker range="vs-2017"

![Framework-Dropdownliste in VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Framework-Dropdownliste in VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

Für ein vorhandenes Projekt können Sie die .NET Framework-Zielversion über das Dialogfeld „Projekteigenschaften“ ändern. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Auflösen von System- und Benutzerassemblyverweisen

Um eine .NET Framework-Version als Ziel zu verwenden, müssen Sie zunächst die entsprechenden Assemblyverweise installieren. Sie können Developer Packs für verschiedene Versionen von .NET Framework auf der Website für [.NET-Downloads](https://www.microsoft.com/net/download/windows) herunterladen.

Über das Dialogfeld **Verweis hinzufügen** werden Systemassemblys deaktiviert, die nicht zur .NET Framework-Zielversion gehören, sodass sie nicht versehentlich zu einem Projekt hinzugefügt werden können. (Systemassemblys sind *DLL*-Dateien, die in einer .NET Framework-Version enthalten sind.) Verweise, die zu einer .NET Framework-Version gehören, die älter ist als die Zielversion, werden nicht aufgelöst, und Steuerelemente, die von einem solchen Verweis abhängen, können nicht hinzugefügt werden. Wenn Sie einen solchen Verweis aktivieren möchten, setzen Sie das .NET Framework-Ziel des Projekts auf eine Version zurück, die den Verweis enthält.  Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Weitere Informationen zu Assemblyverweisen finden Sie unter [Auflösen von Assemblys zur Entwurfszeit](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Aktivieren von LINQ

Wenn Sie .NET Framework 3.5 oder eine höhere Version als Ziel verwenden, werden automatisch ein Verweis auf **System.Core** und ein Import auf Projektebene für <xref:System.Linq> (nur in Visual Basic) hinzugefügt. Wenn Sie LINQ-Features verwenden möchten, müssen Sie zusätzlich `Option Infer` aktivieren (nur in Visual Basic). Der Verweis und der Import werden automatisch entfernt, wenn Sie die Zielversion auf eine frühere .NET Framework-Version ändern. Weitere Informationen finden Sie unter [Arbeiten mit LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Siehe auch

- [Projekte für mehrere Zielframeworkversionen (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Vorgehensweise: How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
---
title: Eine Version von .NET als Ziel
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET [Visual Studio]
- .NET version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c316610fc007e3e8642567c01a5172feb461bda
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747123"
---
# <a name="how-to-target-a-version-of-net"></a>Vorgehensweise: Eine Version von .NET als Ziel

Dieser Artikel beschreibt, wie Sie eine bestimmte Version von .NET Framework abzielen, wenn Sie ein Projekt .NET Framework erstellen. Ferner wird beschrieben, wie die Zielversion in einem vorhandenen Visual Basic-, C#- oder F#-Projekt geändert werden kann.

> [!IMPORTANT]
> Informationen darüber, wie Sie die Zielversion für C++-Projekte ändern können, finden Sie unter [How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Festlegen einer Zielversion beim Erstellen eines Projekts

Wenn Sie ein Projekt .NET Framework erstellen, hängen die verfügbaren Versionen von .NET Framework, welche Versionen installiert sind und der ausgewählten Projektvorlage.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

1. Wählen Sie eine .NET Framework-Vorlage für den Typ des Projekts, das Sie erstellen möchten.

1. Wählen Sie in der Dropdownliste **Framework** unten im Dialogfeld die gewünschte .NET Framework-Zielversion für Ihr Projekt aus.

   Die Liste der Frameworks zeigt nur die Versionen an, die auf die von Ihnen ausgewählte Vorlage anwendbar sind.

   > [!NOTE]
   > Einige Projekttypen wie .NET Core, werden nicht angezeigt. die **Framework** Dropdown-Liste.

   ::: moniker range="vs-2017"

   ![Framework-Dropdownliste im Dialogfeld "Neues Projekt" Visual Studio 2017](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Framework-Auswahl in Visual Studio 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Fahren Sie mit der [Projekterstellung](create-new-project.md) fort.

## <a name="change-the-targeted-version"></a>Ändern der Zielversion

Sie können die Zielversion von .NET in einer Visual Basic ändern C#, oder F# Projekt mithilfe des folgenden Verfahrens.

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das zu ändernde Projekt, und wählen Sie **Eigenschaften** aus.

    ![Visual Studio Eigenschaften des Projektmappen-Explorer](../ide/media/vs_slnexplorer_properties.png)

1. Klicken Sie in der linken Spalte des Fensters **Eigenschaften** auf die Registerkarte **Anwendung**.

    ![Visual Studio, App-Eigenschaften, Registerkarte "Anwendung"](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Nachdem Sie eine UWP-app erstellt haben, können nicht Sie die Zielversion von .NET oder Windows ändern.

1. Wählen Sie in der Liste **Zielframework** die gewünschte Zielversion aus.

1. Wählen Sie im daraufhin angezeigten Überprüfungsdialogfeld die Schaltfläche **Ja** aus.

    Das Projekt wird entladen. Beim erneuten Laden, ist es die .NET Version, die Sie soeben ausgewählt haben.

    > [!NOTE]
    > Wenn Ihr Code Verweise auf eine andere Version von .NET als das enthält, die Sie ausgerichtet, möglicherweise Fehlermeldungen angezeigt, beim Kompilieren oder führen Sie den Code. Um diese Fehler zu beheben, müssen Sie die Verweise ändern. Finden Sie unter [Problembehandlung bei .NET Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Siehe auch

- [Übersicht über .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Problembehandlung bei .NET Framework-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Vorgehensweise: How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
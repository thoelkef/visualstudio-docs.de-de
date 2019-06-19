---
title: Ausrichten auf eine .NET-Version
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
# <a name="how-to-target-a-version-of-net"></a>Vorgehensweise: Ausrichten auf eine Version von .NET

In diesem Artikel wird beschrieben, wie Sie beim Erstellen eines .NET Framework-Projekts eine bestimmte .NET Framework-Zielversion festlegen. Ferner wird beschrieben, wie die Zielversion in einem vorhandenen Visual Basic-, C#- oder F#-Projekt geändert werden kann.

> [!IMPORTANT]
> Informationen darüber, wie Sie die Zielversion für C++-Projekte ändern können, finden Sie unter [How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Festlegen einer Zielversion beim Erstellen eines Projekts

Welche .NET Framework-Versionen beim Erstellen eines .NET Framework-Projekts verfügbar sind, richtet sich danach, welche Versionen installiert sind und welche Projektvorlage ausgewählt ist.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

1. Wählen Sie eine .NET Framework-Vorlage für den Projekttyp aus, den Sie erstellen möchten.

1. Wählen Sie in der Dropdownliste **Framework** unten im Dialogfeld die gewünschte .NET Framework-Zielversion für Ihr Projekt aus.

   Die Liste der Frameworks zeigt nur die Versionen an, die auf die von Ihnen ausgewählte Vorlage anwendbar sind.

   > [!NOTE]
   > Einige Projekttypen, z.B. .NET Core, zeigen die Dropdownliste **Framework** nicht an.

   ::: moniker range="vs-2017"

   ![Framework-Dropdownliste im Visual Studio 2017-Dialogfeld „Neues Projekt“](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Framework-Auswahl in Visual Studio 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Fahren Sie mit der [Projekterstellung](create-new-project.md) fort.

## <a name="change-the-targeted-version"></a>Ändern der Zielversion

Führen Sie die folgenden Schritte aus, um die .NET-Zielversion in einem Visual Basic-, C#- oder F#-Projekt zu ändern.

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das zu ändernde Projekt, und wählen Sie **Eigenschaften** aus.

    ![Visual Studio Eigenschaften des Projektmappen-Explorer](../ide/media/vs_slnexplorer_properties.png)

1. Klicken Sie in der linken Spalte des Fensters **Eigenschaften** auf die Registerkarte **Anwendung**.

    ![Visual Studio, App-Eigenschaften, Registerkarte "Anwendung"](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Nachdem Sie eine UWP-App erstellt haben, können Sie weder die Windows-Zielversion noch die .NET-Zielversion ändern.

1. Wählen Sie in der Liste **Zielframework** die gewünschte Zielversion aus.

1. Wählen Sie im daraufhin angezeigten Überprüfungsdialogfeld die Schaltfläche **Ja** aus.

    Das Projekt wird entladen. Wenn es erneut geladen wird, verwendet es die .NET-Zielversion, die Sie soeben ausgewählt haben.

    > [!NOTE]
    > Sollte der Code Verweise auf eine .NET-Version enthalten, die nicht die Zielversion ist, werden möglicherweise Fehlermeldungen angezeigt, wenn Sie den Code kompilieren oder ausführen. Um diese Fehler zu beheben, müssen Sie die Verweise ändern. Weitere Informationen finden Sie unter [Problembehandlung bei .NET-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Siehe auch

- [Übersicht über Frameworkziele](../ide/visual-studio-multi-targeting-overview.md)
- [Problembehandlung bei .NET Framework-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Vorgehensweise: How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
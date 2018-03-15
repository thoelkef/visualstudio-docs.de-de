---
title: "Erstellen von Projekten für eine bestimmte .NET Framework-Version in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 02/06/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 03d8b734833fad5a47f0d5517b21a7851d9258a6
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Gewusst wie: Erstellen von Projekten für eine bestimmte .NET Framework-Version

In diesem Dokument wird beschrieben, wie Sie ein Projekt für eine bestimmte .NET Framework-Version erstellen und wie diese Zielversion in vorhandenen Visual Basic-, C#- oder Visual F#-Projekten geändert werden kann.

> [!IMPORTANT]
> Weitere Informationen zum Ändern der Zielversion für C++-Projekte finden Sie unter [Vorgehensweise: Ändern des Zielframeworks und Plattformtoolset](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="to-target-a-version-when-you-create-a-project"></a>So richten Sie ein Projekt bei der Erstellung auf eine Zielversion aus

Welche .NET Framework-Versionen verfügbar sind, wenn Sie ein Projekt erstellen, hängt davon ab, welche Versionen installiert sind, und von der im Dialogfeld **Neues Projekt** ausgewählten Vorlage.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt...**.

1. Wählen Sie in der Liste der installierten Vorlagen den Projekttyp aus, den Sie erstellen möchten, und geben Sie einen Namen für das Projekt ein.

1. Wählen Sie in der Dropdownliste **Framework** unten im Dialogfeld **Neues Projekt** die gewünschte .NET Framework-Version für Ihr Projekt aus.

    Die Liste der Frameworks zeigt nur die Versionen an, die auf die von Ihnen ausgewählte Vorlage anwendbar sind. Einige Projekttypen, z.B. .NET Core, erfordern kein .NET Framework. In solchen Fällen ist die **Framework**-Dropdownliste ausgeblendet.

    ![Framework-Dropdownliste im Dialogfeld „Neues Projekt“](media/vside-newproject-framework.png)

1. Klicken Sie auf die Schaltfläche **OK** .

## <a name="to-change-the-targeted-version"></a>So ändern Sie die Zielversion

Die folgenden Schritte zeigen, wie eine .NET Framework-Zielversion in einem vorhandenen Visual Basic-, C#- oder Visual F#-Projekt geändert wird.

Weitere Informationen zum Ändern der Zielversion für C++-Projekte finden Sie unter [Vorgehensweise: Ändern des Zielframeworks und Plattformtoolset](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das zu ändernde Projekt, und wählen Sie **Eigenschaften** aus.

    ![Visual Studio Eigenschaften des Projektmappen-Explorer](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")

1. Im linken Bereich des Fensters Eigenschaften wählen Sie die Registerkarte **Anwendung** aus.

    ![Visual Studio, App-Eigenschaften, Registerkarte „Anwendung“](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Nachdem Sie eine UWP-App erstellt haben, können Sie weder die Windows-Zielversion noch die .NET Framework-Zielversion ändern.

1. Wählen Sie in der Liste **Zielframework** die gewünschte Zielversion aus.

1. Wählen Sie im daraufhin angezeigten Überprüfungsdialogfeld die Schaltfläche **Ja** aus.

    Das Projekt wird entladen. Wenn es erneut geladen wird, verwendet es die .NET Framework-Zielversion, die Sie soeben ausgewählt haben.

    > [!NOTE]
    > Sollte der Code Verweise auf eine .NET Framework-Version enthalten, die nicht die Zielversion ist, werden möglicherweise Fehlermeldungen angezeigt, wenn Sie den Code kompilieren oder ausführen. Um diese Fehler zu beheben, müssen Sie die Verweise ändern. Weitere Informationen finden Sie unter [Problembehandlung bei .NET Framework-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Siehe auch

[Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../ide/visual-studio-multi-targeting-overview.md)  
[Problembehandlung bei .NET Framework-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)  
[Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)  
[Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
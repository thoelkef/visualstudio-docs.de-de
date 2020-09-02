---
title: 'Vorgehensweise: .NET Framework-Version als Ziel | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7aae21e2c959939262b88db3b90367c4860d8a74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670619"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Gewusst wie: .NET Framework-Version als Ziel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird beschrieben, wie eine bestimmte .NET Framework-Version für ein Projekt gewählt wird und wie diese Zielversion in vorhandenen Visual Basic-, Visual C#- oder Visual F#-Projekten geändert werden kann.

> [!IMPORTANT]
> Weitere Informationen zum Ändern der Zielversion für C++-Projekte finden Sie unter [Vorgehensweise: Ändern des Zielframeworks und Plattformtoolset](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

 **Inhalt**

- [Ziel einer Version beim Erstellen eines Projekts](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)

- [Ändern der Zielversion](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)

## <a name="targeting-a-version-when-you-create-a-project"></a><a name="bkmk_new"></a> Projekt für eine Zielversion erstellen
 Wenn Sie ein Projekt erstellen, bestimmt die Version von .NET Framework, auf die Sie abzielen, die Vorlagen, die Sie verwenden können.

> [!NOTE]
> In den Express-Editionen von Visual Studio müssen Sie zuerst das Projekt erstellen und können dann erst die Zielversion ändern, wie unter [Ändern der Zielversion](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) weiter unten in diesem Thema beschrieben.

#### <a name="to-target-a-version-when-you-create-a-project"></a>So richten Sie ein Projekt bei der Erstellung auf eine Zielversion aus

1. Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.

2. Wählen Sie in der Liste oben im Dialogfeld **Neues Projekt** die gewünschte .NET Framework-Version für Ihr Projekt aus.

    > [!NOTE]
    > In der Regel wird nur eine .NET Framework-Version zusammen mit Visual Studio installiert. Wenn Sie eine andere Zielversion verwenden möchten, müssen Sie zunächst sicherstellen, dass diese installiert ist. Weitere Informationen finden Sie in der [Übersicht über die Ausrichtung auf mehrere Zielversionen in Visual Studio](../ide/visual-studio-multi-targeting-overview.md).

3. In der Liste der installierten Vorlagen wählen Sie den Typ des Projekts aus, das Sie erstellen möchten, benennen das Projekt und wählen dann die Schaltfläche **OK**.

     In der Liste der Vorlagen werden nur die Projekte angezeigt, die von der ausgewählten .NET Framework-Version unterstützt werden.

## <a name="changing-the-target-version"></a><a name="bkmk_existing"></a> Ändern der Zielversion
 Die folgenden Schritte zeigen, wie eine .NET Framework-Zielversion in einem vorhandenen Visual Basic-, Visual C#- oder Visual F#-Projekt geändert wird.

#### <a name="to-change-the-targeted-version"></a>So ändern Sie die Zielversion

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das zu ändernde Projekt, und wählen Sie **Eigenschaften** aus.

     ![Visual Studio Eigenschaften des Projektmappen-Explorer](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")

    > [!IMPORTANT]
    > Weitere Informationen zum Ändern der Zielversion für C++-Projekte finden Sie unter [Vorgehensweise: Ändern des Zielframeworks und Plattformtoolset](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

2. Wählen Sie in der linken Spalte des Fensters Eigenschaften die Registerkarte **Anwendung** aus.

     ![Visual Studio, App-Eigenschaften, Registerkarte "Anwendung"](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Nachdem Sie eine Windows Store-App in Visual Studio 2013 erstellt haben, können Sie weder die Windows-Zielversion noch die .NET Framework-Zielversion ändern.

3. Wählen Sie in der Liste **Zielframework** die gewünschte Zielversion aus.

4. Wählen Sie im daraufhin angezeigten Überprüfungsdialogfeld die Schaltfläche **Ja** aus.

     Das Projekt wird entladen. Wenn es erneut geladen wird, verwendet es die .NET Framework-Zielversion, die Sie soeben ausgewählt haben.

    > [!NOTE]
    > Sollte der Code Verweise auf eine .NET Framework-Version enthalten, die nicht die Zielversion ist, werden möglicherweise Fehlermeldungen angezeigt, wenn Sie den Code kompilieren oder ausführen. Um diese Fehler zu beheben, müssen Sie die Verweise ändern. Weitere Informationen finden Sie unter [Problembehandlung bei .NET Framework-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Weitere Informationen
 [Übersicht über die Ausrichtung auf mehrere Ziel Versionen in Visual Studio](../ide/visual-studio-multi-targeting-overview.md) .NET Framework die Festlegung von Ziel Versionen [für ASP.NET-Webprojekte](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) [Problembehandlung .NET Framework Ziel Fehler](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md) [Anwendungsseite, Projekt-Designer (c#)](../ide/reference/application-page-project-designer-csharp.md) [Anwendungsseite, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [Konfigurieren von Projekten](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526) Gewusst [wie: Ändern des Ziel-Frameworks](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)

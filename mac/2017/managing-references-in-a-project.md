---
title: Verwalten von Verweisen in einem Projekt
description: In diesem Artikel erfahren Sie, wie Sie Verweise in einem Projekt in Visual Studio für Mac verwalten können.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: f9925954083c7fe64ad29c7cfed618a84d7a6386
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984862"
---
# <a name="managing-references-in-a-project"></a>Verwalten von Verweisen in einem Projekt

Visual Studio für Mac bietet zwei Möglichkeit zum Hinzufügen von zusätzlichen Verweisen zu Ihrem Projekt:

![Projektverweise](media/projects-and-solutions-image10.png)

Dies sind:

* References
* NuGets (hinzufügbar über den Ordner „Pakete“)

Darüber hinaus können zu jedem Projekt auch Webverweise und native Verweise hinzufügt werden.

## <a name="assembly-references"></a>Assemblyverweise

Jedes Framework innerhalb von Xamarin umfasst über ein Dutzend Assemblys. Nicht auf alle dieser Assemblypakete wird standardmäßig in Ihrem Projekt verwiesen.

Sie können über das Dialogfeld **Verweise bearbeiten** Pakete bearbeiten, auf die in Ihrem Projekt verwiesen wird. Das Dialogfeld kann durch Doppelklicken auf den Ordner „Verweise“ angezeigt werden oder indem Sie in den Kontextmenüaktionen auf **Verweise bearbeiten** klicken:

![Dialogfeld „Assemblyverweise“](media/projects-and-solutions-image11.png)

Weitere Informationen zu den Assemblys, die für jedes Xamarin-Framework verfügbar sind, finden Sie im Leitfaden für [Available Assemblies (verfügbare Assemblys)](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet ist der beliebteste Paket-Manager für die .NET-Entwicklung. Die NuGet-Unterstützung von Visual Studio für Mac ermöglicht Ihnen die Suche nach Paketen, die Sie Ihrem Projekt hinzufügen können.

Klicken Sie dazu mit der rechten Maustaste auf den Ordner **Pakete** im Projektmappenpad, und klicken Sie dann auf „Pakete hinzufügen“.

Weitere Informationen zur Verwendung eines NuGet-Pakets finden Sie in der exemplarischen Vorgehensweise [Including a NuGet package in your Project (Einfügen eines NuGet-Pakets in Ihr Projekt)](nuget-walkthrough.md).

## <a name="see-also"></a>Weitere Informationen

- [Verwalten von Verweisen (Visual Studio unter Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Hinzufügen von Verweisen mithilfe von NuGet im Vergleich zu einer SDK-Erweiterung (Visual Studio unter Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)
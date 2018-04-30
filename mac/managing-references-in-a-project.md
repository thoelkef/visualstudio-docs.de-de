---
title: Verwalten von Verweisen in einem Projekt in Visual Studio für Mac
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 75395ed0d97eba5203adf7de384bb60f71313916
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="managing-references-in-a-project"></a>Verwalten von Verweisen in einem Projekt

Visual Studio für Mac bietet zwei Möglichkeit zum Hinzufügen von zusätzlichen Verweisen zu Ihrem Projekt:

![Projektverweise](media/projects-and-solutions-image10.png)

Diese lauten wie folgt:

* Verweise
* NuGets (hinzufügbar über den Ordner „Pakete“)

Darüber hinaus können zu jedem Projekt auch Webverweise und native Verweise hinzufügt werden.

## <a name="assembly-references"></a>Assemblyverweise

Jedes Framework innerhalb von Xamarin umfasst über ein Dutzend Assemblys. Nicht auf alle dieser Assemblypakete wird standardmäßig in Ihrem Projekt verwiesen. 

Verwenden Sie das Dialogfeld _Verweise bearbeiten_, um Pakete zu bearbeiten, auf die in Ihrem Projekt verwiesen wird. Dieses kann durch Doppelklicken auf den Ordner „Verweise“ angezeigt werden oder indem sie auf „Verweise bearbeiten“ in den Kontextmenüaktionen klicken:

![Dialogfeld „Assemblyverweise“](media/projects-and-solutions-image11.png)

Weitere Informationen zu den Assemblys, die für jedes Xamarin-Framework verfügbar sind, finden Sie im Leitfaden für [Available Assemblies (verfügbare Assemblys)](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet ist der beliebteste Paket-Manager für die .NET-Entwicklung. Die NuGet-Unterstützung von Visual Studio für Mac ermöglicht Ihnen die Suche nach Paketen, die Sie Ihrem Projekt hinzufügen können.

Klicken Sie dazu mit der rechten Maustaste auf den Ordner **Pakete** im Projektmappenpad, und klicken Sie dann auf „Pakete hinzufügen“.

Weitere Informationen zur Verwendung eines NuGet-Pakets finden Sie in der exemplarischen Vorgehensweise [Including a NuGet package in your Project (Einfügen eines NuGet-Pakets in Ihr Projekt)](~/nuget-walkthrough.md).

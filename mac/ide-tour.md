---
title: "Visual Studio für Mac – Überblick | Microsoft-Dokumentation"
description: "Visual Studio für Mac bietet eine integrierte Entwicklungsumgebung zum Erstellen von .NET-Anwendungen unter macOS. Dazu gehören ASP.NET Core-Websites und Xamarin-Projekte für iOS, Android, Mac und Xamarin.Forms."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.openlocfilehash: 0f8f3ba04d4e5a8949bc57cb8cf61d470690d786
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-for-mac-tour"></a>Visual Studio für Mac: Überblick

Visual Studio für Mac entwickelt die für mobile Geräte konzipierte IDE von Xamarin, Xamarin Studio, zu einer Mobile-First-, Cloud-First-Entwicklungsumgebung auf dem Mac weiter. Mit diesem auf Entwickler ausgerichteten Tool können Sie die Leistung von .NET nutzen, um Anwendungen für alle Plattformen zu erstellen, die Ihr Benutzer benötigt.

Die Benutzererfahrung von Visual Studio für Mac ähnelt der des Produkts für Windows, allerdings mit dem typischen macOS-Gefühl. Das Erstellen, Öffnen und Entwickeln einer Anwendung ist eine vertraute Erfahrung für jeden, der schon einmal Visual Studio unter Windows verwendet hat. Zusätzlich werden auch in Visual Studio für Mac die leistungsstarken Tools eingesetzt, die sein Windows-Pendant zu einer derartig leistungsfähigen IDE machen. Die Roslyn-Compilerplattform wird für das Refactoring und IntelliSense verwendet. Das Projektsystem und Buildmodul verwenden MSBuild. Der Quell-Editor unterstützt TextMate-Bündel. Das Produkt verwendet die gleichen Debuggermodule für Xamarin- und .NET Core-Apps und die gleichen Designer für Xamarin.iOS und Xamarin.Android.

Dieser Artikel behandelt verschiedene Abschnitte von Visual Studio für Mac, um einen Einblick in einige der Features zu geben, die es zu einem leistungsstarken Tool zur Erstellung von plattformübergreifenden Anwendungen macht.

## <a name="ide-tour"></a>IDE-Überblick

Visual Studio für Mac ist in verschiedenen Abschnitten zum Verwalten von Anwendungsdateien und -einstellungen und zum Erstellen und Debuggen von Code organisiert.

## <a name="welcome-screen"></a>Willkommensseite

Wenn Visual Studio für Mac gestartet wird, wird diese *Willkommensseite* angezeigt:

![Willkommensseite](media/ide-tour-image1.png)

Die Wilkommensseite enthält folgende Abschnitte:

- **Symbolleiste**: bietet schnellen Zugriff auf die Suchleiste. Wenn eine Projektmappe geladen wird, wird dies verwendet, um App-Konfigurationen vorzunehmen, zum Debuggen und zum Anzeigen von Fehlern.
- **Erste Schritte**: bietet schnellen Zugriff auf nützliche Themen für Entwickler, die gerade mit der Arbeit mit Visual Studio für Mac beginnen.
- **Zuletzt verwendete Projektmappen**: bietet schnellen Zugriff auf zuletzt geöffnete Projektmappen sowie praktische Schaltflächen zum Öffnen und Erstellen von Projekten.
- **Neuigkeiten für Entwickler**: Ein Newsfeed, mit dem Sie immer auf dem neuesten Stand sind, was Informationen für Microsoft-Entwickler angeht.

## <a name="solutions-and-projects"></a>Projektmappen und Projekte

Das Bild unten zeigt Visual Studio für Mac mit einer geladenen Anwendung:

![Visual Studio für Mac mit einer geladenen Anwendung](media/ide-tour-image17.png)

In den folgenden Abschnitten wird ein Überblick über die Hauptbereich von Visual Studio für Mac gegeben.

## <a name="solution-pad"></a>Projektmappenpad

Das Projektmappenpad organisiert die Projekte in Ihrer Projektmappe wie unten gezeigt:

![Im Projektmappenpad organisierte Projekte](media/ide-tour-image18.png)

Hier werden Dateien für den Quellcode, Ressourcen, Benutzeroberflächen und Abhängigkeiten in plattformspezifische Projekte organisiert.

Weitere Informationen zum Verwenden von Projekten und Projektmappen in Visual Studio für Mac finden Sie unter [Projektmappen und Projekte](~/projects-and-solutions.md).

## <a name="assembly-references"></a>Assemblyverweise
 
Assemblyverweise für jedes Projekt stehen im Ordner „Verweise“ zu Verfügung, wie unten gezeigt:

![Ordner „Verweise“ im Projektmappenpad](media/ide-tour-image19.png)

Sie können mit dem Dialogfeld **Verweise bearbeiten** zusätzliche Verweise hinzufügen. Dieses kann durch Doppelklicken auf den Ordner „Verweise“ angezeigt werden, oder indem Sie auf **Verweise bearbeiten** in den Kontextmenüaktionen klicken:
 
![Dialogfeld „Verweise bearbeiten“](media/ide-tour-image20.png)

Weitere Informationen zum Verwenden von Verweisen in Visual Studio für Mac finden Sie unter [Verwalten von Verweisen in einem Projekt](~/managing-references-in-a-project.md).

## <a name="dependencies--packages"></a>Abhängigkeiten/Pakete

Alle externen Abhängigkeiten, die in Ihrer Anwendung verwendet werden, werden in dem Ordner „“ oder in dem Ordner „“ gespeichert, je nachdem, ob Sie sich in einem Projekt von .NET Core oder Xamarin.iOS bzw. Xamarin.Android. Diese werden entweder als NuGet oder als Komponente bereitgestellt.

NuGet ist der beliebteste Paket-Manager für die .NET-Entwicklung. Mit der NuGet-Unterstützung von Visual Studio können Sie leicht nach Paketen suchen und diese in Ihrer Anwendung einem Projekt hinzufügen.

Um Ihrer Anwendung eine Abhängigkeit hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Ordner Abhängigkeiten/Pakete und dann auf **Pakete hinzufügen**.

![Hinzufügen eines NuGet-Pakets](media/ide-tour-image21.png)

Informationen zum Verwenden eines NuGet-Pakets in einer Anwendung finden Sie unter [Including a NuGet project in your project (Verwenden eines NuGet-Pakets in Ihrem Projekt)](~/nuget-walkthrough.md).

## <a name="refactoring"></a>Umgestaltung

Visual Studio für Mac bietet zwei praktische Möglichkeiten zum Umgestalten Ihres Codes: Kontextaktionen und Quellanalysen. Weitere Informationen finden Sie unter [Refactoring](~/refactoring.md).

## <a name="debugging"></a>Debuggen

Visual Studio für Mac besitzt einen nativen Debugger, der das Debuggen für Xamarin.iOS-, Xamarin.Mac- und Xamarin.Android-Anwendungen unterstützt. Visual Studio für Mac verwendet den Soft-Debugger von Mono, der in die Mono-Laufzeit integriert wird und es Visual Studio für Mac ermöglicht, verwalteten Code für alle Plattformen zu debuggen. Weitere Informationen zum Debuggen finden Sie unter [Debugging](~/debugging.md).

Der Debugger enthält umfangreiche Schnellansichten für besondere Typen wie Zeichenfolgen, Farben, und URLs sowie Größen, Koordinaten und Bézierkurven.

Weitere Informationen zu den Datenschnellansichten des Debuggers finden Sie unter [Data Visualizations (Datenschnellansichten)](~/data-visualizations.md).

## <a name="version-control"></a>Quellcodeverwaltung

Visual Studio für Mac kann in die Quellcodeverwaltungs-Systeme Git und Subversion integriert werden. Projekte unter Quellcodeverwaltung werden mit dem Branch bezeichnet, der neben dem Namen der Projektmappe angezeigt wird: 

![Branchname, der ein Projekt unter Quellcodeverwaltung angibt](media/ide-tour-image22.png)

Dateien mit ausgecheckten Änderungen haben eine Bemerkung an ihrem Symbol im Projektmappenbereich, wie unten gezeigt:

![Ausgecheckte Dateien im Projektmappenpad](media/ide-tour-image23.png)

Weitere Informationen zum Verwenden der Versionskontrolle in Visual Studio finden Sie unter [Versionskontrolle](~/version-control.md).
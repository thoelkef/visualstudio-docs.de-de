---
title: "Kompilieren und Erstellen in Visual Studio für Mac | Microsoft Dokumentation"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 9005cf64f4b72f39923d6525e78de745d79c3953
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilieren und Generieren in Visual Studio für Mac

Mit Visual Studio für Mac können Sie Anwendungen und Assemblys während der Entwicklung Ihres Projekts erstellen. Es ist wichtig, Ihren Code früh und häufig zu kompilieren und zu erstellen, damit Sie Typenkonflikte und andere Kompilierzeitfehler identifizieren können.

## <a name="choosing-a-build-method"></a>Auswählen einer Erstellungsmethode

### <a name="using-the-ide"></a>Verwenden von IDE

Mit Visual Studio für Mac können Sie Builds erstellen und umgehend ausführen, während Sie weiterhin die Kontrolle über Buildfunktionen haben. Visual Studio für Mac verwendet MSBuild als zugrundeliegendes Buildsystem.

Alle Projekte und Projektmappen, die in der IDE erstellt werden, weisen eine Standardbuildkonfiguration auf, die den Kontext des Builds definiert. Diese Konfigurationen können bearbeitet werden, oder Sie können Sie selbst erstellen. Das Erstellen oder Modifizieren dieser Konfigurationen aktualisiert automatisch die Projektdatei, die dann von MSBuild verwendet wird, um das Projekt zu erstellen.  

Weitere Informationen zum Erstellen Ihrer eigenen Projekte und Projektmappen in der IDE finden Sie im Handbuch [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](~/building-and-cleaning-projects-and-solutions.md).

Mit Visual Studio für Mac können Sie auch:

* Den Ausgabepfad ändern. Diesen können Sie in den Optionen Ihres Projekts bearbeiten.

    ![Ändern des Ausgabepfads](media/compiling-and-building-image4.png)

* Den Ausführlichkeitsgrad der Buildausgabe ändern:

    ![Ändern des Ausführlichkeitsgrads des Builds](media/compiling-and-building-image5.png)

* Benutzerdefinierte Befehle vor, während oder nach dem Erstellen oder Bereinigen hinzufügen:

    ![Hinzufügen benutzerdefinierter Befehle](media/compiling-and-building-image6.png)

### <a name="building-from-command-line"></a>Erstellen über die Befehlszeile

Sie können Buildmodule von MSBuild verwenden, um Anwendungen über die Befehlszeile zu erstellen.

Weitere Informationen zum Verwenden von MSBuild finden Sie in den Artikeln zu [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

### <a name="using-visual-studio-team-services"></a>Verwenden von Visual Studio Team Services

* [Erstellen Ihrer Xamarin-App](https://www.visualstudio.com/docs/build/apps/mobile/xamarin)
* [Fortlaufende Integration in Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)
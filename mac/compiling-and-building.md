---
title: "Kompilieren und Erstellen in Visual Studio für Mac | Microsoft Dokumentation"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: abf772f1e00239b3a66e01c95dd827a392a12902
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilieren und Generieren in Visual Studio für Mac

Mit Visual Studio für Mac können Sie Anwendungen und Assemblys während der Entwicklung Ihres Projekts erstellen. Es ist wichtig, Ihren Code früh und häufig zu kompilieren und zu erstellen, damit Sie Typenkonflikte und andere Kompilierzeitfehler identifizieren können.

## <a name="building-from-the-ide"></a>Erstellen aus der IDE

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

## <a name="building-from-command-line"></a>Erstellen über die Befehlszeile

Sie können Buildmodule von MSBuild verwenden, um Anwendungen über die Befehlszeile zu erstellen.

Weitere Informationen zum Verwenden von MSBuild finden Sie in den Artikeln zu [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

## <a name="building-from-visual-studio-team-services"></a>Erstellen von Visual Studio Team Services aus

* [Erstellen Ihrer Xamarin-App](https://www.visualstudio.com/docs/build/apps/mobile/xamarin)
* [Fortlaufende Integration in Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)
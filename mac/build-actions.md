---
title: Buildvorgänge
description: In diesem Artikel erfahren Sie mehr über die verschiedenen Buildvorgänge, die für C#-Projekte verwendet werden können.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 889414d391a4a894879399317d782df58a8bacb3
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33865005"
---
# <a name="build-actions"></a>Buildvorgänge

Alle Dateien in einem Projekt in Visual Studio für Mac verfügen über einen Buildvorgang, der steuert, was mit den Dateien während eines Builds geschieht. Diese können festgelegt werden, indem Sie mit der rechten Maustaste auf eine beliebige Datei klicken und wie unten dargestellt zu **Build Action** (Buildvorgang) navigieren:

![Auswählen des Buildvorgangs „Compile“ aus dem Projektmappen-Explorer](media/projects-and-solutions-image1.png)

Im Folgenden finden Sie einige gängige Buildvorgänge für C#-Projekte:

* **None** (Keine): Die Datei ist in keiner Weise Teil des Builds, sondern ist nur für einen leichten Zugriff aus der IDE in das Projekt integriert.
* **Compile** (Kompilieren): Die Datei wird an den C#-Compiler als Quelldatei übergeben.
* **EmbeddedResource**: Die Datei wird an den C#-Compiler als Ressource übergeben, die in die Assembly eingebettet wird. Der Namespace `System.Reflection` kann dann verwendet werden, um die Datei aus einer Assembly zu lesen.
* **Content** (Inhalt): Bei ASP.NET-Projekten werden diese Dateien bei der Bereitstellung als Teil der Website integriert. Bei Xamarin.iOS- und Xamarin.Mac-Projekten sind diese im App-Bundle enthalten.

Es ist möglich, mehr als eine Datei im Projektmappen-Explorer auszuwählen, sodass Sie die Buildvorgänge für viele Dateien auf einmal festlegen können.

Es gibt auch Buildvorgänge für bestimmte Projekte. Xamarin.iOS-Projekte besitzen beispielsweise den Buildvorgang **BundleResource**, wodurch die Datei dem App-Bundle hinzugefügt wird. Weitere Informationen zu bestimmten Buildvorgängen für Xamarin.Android finden Sie im Leitfaden zu [Buildprozessen](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).
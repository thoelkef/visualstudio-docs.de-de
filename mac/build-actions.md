---
title: Buildvorgänge
description: In diesem Artikel erfahren Sie mehr über die verschiedenen Buildvorgänge, die für C#-Projekte verwendet werden können.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: a5b1175caf0ac7f6654fbe20b5300327679eccbc
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294291"
---
# <a name="build-actions"></a>Buildvorgänge

Sämtliche Dateien in einem Projekt von Visual Studio für Mac verfügen über einen Buildvorgang. Dieser steuert, was während eines Builds mit der Datei geschieht. Dieses Verhalten kann festgelegt werden, indem Sie mit der rechten Maustaste auf eine beliebige Datei klicken und wie unten dargestellt zu **Buildvorgang** navigieren:

![Auswählen des Buildvorgangs „Compile“ aus dem Projektmappen-Explorer](media/projects-and-solutions-image1.png)

Im Folgenden finden Sie einige gängige Buildvorgänge für C#-Projekte:

* **None** (Keine): Die Datei ist in keiner Weise Teil des Builds. Sie ist für einen leichten Zugriff über die IDE in das Projekt integriert.
* **Compile** (Kompilieren): Die Datei wird an den C#-Compiler als Quelldatei übergeben.
* **EmbeddedResource**: Die Datei wird an den C#-Compiler als Ressource übergeben, die in die Assembly eingebettet wird. [Assembly.GetManifestResourceStream](https://docs.microsoft.com/dotnet/api/system.reflection.assembly.getmanifestresourcestream), aus dem Namespace `System.Reflection`, kann anschließend zum Lesen der Datei aus der Assembly verwendet werden.
* **Content** (Inhalt): Bei ASP.NET-Projekten werden diese Dateien bei der Bereitstellung als Teil der Website integriert. Bei Xamarin.iOS- und Xamarin.Mac-Projekten sind diese im App-Bundle enthalten.

Im Projektmappen-Explorer können mehrere Dateien ausgewählt werden, sodass Sie die Buildvorgänge für viele Dateien gleichzeitig festlegen können.

Es gibt auch Buildvorgänge für bestimmte Projekte. Xamarin.iOS-Projekte besitzen beispielsweise den Buildvorgang **BundleResource**, wodurch die Datei zum App-Bundle hinzugefügt wird. Weitere Informationen zu bestimmten Buildvorgängen für Xamarin.Android finden Sie im Leitfaden zu [Buildprozessen](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).
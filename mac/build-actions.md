---
title: Buildvorgänge
description: In diesem Artikel erfahren Sie mehr über die verschiedenen Buildvorgänge, die für C#-Projekte verwendet werden können.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714402"
---
# <a name="build-actions"></a>Buildvorgänge

Sämtliche Dateien in einem Projekt von Visual Studio für Mac verfügen über einen Buildvorgang. Die Buildaktion steuert, was während des Builds mit der Datei geschieht. 

>[!NOTE]
>Dieses Thema gilt für Visual Studio für Mac. Informationen für Visual Studio unter Windows finden Sie unter [Buildaktionen](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Festlegen eines Buildprozesses

Sie können wie im Folgenden gezeigt mit der rechten Maustaste auf eine beliebige Datei klicken und zu **Buildaktionen** navigieren, um eine Buildaktion für eine Datei in Visual Studio für Mac festzulegen:

![Auswählen des Buildvorgangs „Compile“ aus dem Projektmappen-Explorer](media/projects-and-solutions-image1.png)

Die Buildaktionen für diese Datei werden im Flyoutmenü angezeigt. 

## <a name="build-action-values"></a>Buildprozesswerte

Zu den gängigen Buildaktionen für Projekte, die Sie in Visual Studio für Mac erstellen können, gehören unter anderem folgende:

|Buildvorgang | Projekttypen | BESCHREIBUNG |
|--|--|--|
| **Compile** | any | Die Datei wird als Quelldatei an den C#-Compiler übergeben.|
| **Inhalt** | .NET, Xamarin | Bei ASP.NET-Projekten werden diese Dateien bei der Bereitstellung als Teil der Website integriert. Bei Xamarin.iOS- und Xamarin.Mac-Projekten sind diese im App-Bundle enthalten.|
| **Embedded Resource** | .NET | Die Datei wird als Ressource an den C#-Compiler übergeben, die in die Assembly eingebettet wird. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), aus dem Namespace `System.Reflection`, kann anschließend zum Lesen der Datei aus der Assembly verwendet werden.|
| **None** | any | Die Datei ist in keiner Weise Teil des Builds. Sie ist für einen leichten Zugriff über die IDE in das Projekt integriert. Dieser Wert kann für Dokumentationsdateien wie Infodateien verwendet werden.|

> [!NOTE]
> Zusätzliche Buildaktionen können für bestimmte Projekttypen definiert werden, sodass die Liste der Buildaktionen vom Projekttyp abhängt und Werte angezeigt werden können, die nicht in dieser Liste enthalten sind.  

Xamarin.iOS-Projekte besitzen beispielsweise den Buildvorgang **BundleResource**, wodurch die Datei zum App-Bundle hinzugefügt wird. Weitere Informationen zu bestimmten Buildvorgängen für Xamarin.Android finden Sie im Leitfaden zu [Buildprozessen](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

Im Projektmappen-Explorer können auch mehrere Dateien ausgewählt werden, sodass Sie die Buildaktionen für viele Dateien gleichzeitig festlegen können.

## <a name="see-also"></a>Weitere Informationen

- [Buildvorgänge (Visual Studio unter Windows)](/visualstudio/ide/build-actions)
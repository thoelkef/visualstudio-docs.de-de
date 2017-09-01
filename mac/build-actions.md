---
title: "Buildvorgänge"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 347378da197b5c6d22bbd145c2ac8673d53a63bf
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---

# <a name="build-actions"></a>Buildvorgänge 

Alle Dateien in einem Projekt in Visual Studio für Mac verfügen über einen Buildvorgang, der steuert, was mit den Dateien während eines Builds geschieht. Diese können festgelegt werden, indem Sie mit der rechten Maustaste auf eine beliebige Datei klicken und wie unten dargestellt zu **Build Action** (Buildvorgang) navigieren:

![](media/projects-and-solutions-image1.png)

Im Folgenden finden Sie einige gängige Buildvorgänge für C#-Projekte:

* **None** (Keine): Die Datei ist in keiner Weise Teil des Builds, sondern ist nur für einen leichten Zugriff aus der IDE in das Projekt integriert.
* **Compile** (Kompilieren): Die Datei wird an den C#-Compiler als Quelldatei übergeben.
* **EmbeddedResource**: Die Datei wird an den C#-Compiler als Ressource übergeben, die in die Assembly eingebettet wird. Der Namespace `System.Reflection` kann dann verwendet werden, um die Datei aus einer Assembly zu lesen.
* **Content** (Inhalt): Bei ASP.NET-Projekten werden diese Dateien bei der Bereitstellung als Teil der Website integriert. Bei Xamarin.iOS- und Xamarin.Mac-Projekten sind diese im App-Bundle enthalten.

Es ist möglich, mehr als eine Datei im Projektmappen-Explorer auszuwählen, sodass Sie die Buildvorgänge für viele Dateien auf einmal festlegen können.

Es gibt auch Buildvorgänge für bestimmte Projekte. Xamarin.iOS-Projekte besitzen beispielsweise den Buildvorgang **BundledResource**, wodurch die Datei dem App-Bundle hinzugefügt wird. Weitere Informationen zu bestimmten Buildvorgängen für Xamarin.Android finden Sie in der Führungslinie zu [build process (Buildprozessen)](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions) unter developer.xamarin.com.

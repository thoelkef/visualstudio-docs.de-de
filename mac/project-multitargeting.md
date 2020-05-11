---
title: Projekte zur Festlegung von Zielversionen
description: Dieses Dokument enthält eine Übersicht über die Einrichtung von Projekten zur Festlegung von Zielversionen in Visual Studio für Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439043"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projekte mit mehreren Zielframeworks
In Visual Studio für Mac können Sie ein Xamarin- oder .NET Core-Projekt so konfigurieren, dass es in einer beliebigen von mehreren Versionen des .NET Frameworks und auf einer beliebigen von mehreren Systemplattformen ausgeführt werden kann. Sie könnten z. B. ein Projekt für die Ausführung sowohl auf .NET Framework 4.6 als auch auf .NET Core 3.1 ausrichten. 

Weitere Informationen zu Zielframeworks finden Sie unter [Zielframeworks](/dotnet/standard/frameworks).

> [!NOTE] 
> Dieses Thema gilt für Visual Studio für Mac. Informationen zu Visual Studio unter Windows finden Sie unter [Übersicht über Frameworkziele](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Ausrichten auf mehrere Zielframeworks

Zielframeworks werden in Ihrer Projektdatei angegeben, die Sie bearbeiten können, indem Sie mit der rechten Maustaste auf Ihr Projekt klicken und den Befehl **Tools > Datei bearbeiten** auswählen. Wenn ein einzelnes Framework angegeben wird, verwenden Sie das Element „TargetFramework“. Die folgende Projektdatei einer Konsolen-App veranschaulicht, wie Sie .NET Core 3.0 als Ziel verwenden können:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Verwenden Sie das Element „TargetFrameworks“ im Plural für mehrere Zielframeworks:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Erfahren Sie mehr darüber, wie Sie [mehrere Frameworks als Ziel verwenden können](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Arbeiten mit Code in einem Projekt zur Festlegung von Zielversionen
Wenn Sie eine C#-Datei in einem Projekt mit mehreren Zielframeworks bearbeiten, können Sie angeben, welches Zielframework Sie verwenden möchten, um Ihre Benutzeroberfläche für den Editor zu steuern (z. B. durch Anzeigen von Warnungen, wenn Sie eine API verwenden, die von diesem Framework nicht unterstützt wird). Sie können das Zielframework ändern, indem Sie den Selektor **Zielframework** in der linken oberen Ecke des Editorfensters verwenden.

![Verwenden des Zielframework-Selektors zum Ändern des Zielframeworks, der sich am oberen Rand des Editorfensters befindet](media/project-multitargeting-framework-selector.png)

Manchmal müssen Sie abhängig von der Plattform, auf die die Anwendung ausgerichtet ist, verschiedene APIs aufzurufen. Dazu können Sie bedingten Code schreiben, um Code für eine bestimmte Plattform zu kompilieren:

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Beim Schreiben von Code werden Warnungen in den Vorschlägen für die automatische IntelliSense-Vervollständigung angezeigt, die Sie darauf hinweisen, wenn bestimmte APIs für eines der von Ihrer Anwendung unterstützten Zielframeworks fehlen.

![Eine in IntelliSense angezeigte Warnmeldung, dass eine API für ein bestimmtes Zielframework nicht verwendet werden kann. Beispieltext: namespace System.Buffers, SharedUtils (netstandard2.0) – Nicht verfügbar. Sie können den Kontext über die Navigationsleiste wechseln.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über Frameworkziele (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Zielframeworks in Projekten im SDK-Format](/dotnet/standard/frameworks#how-to-specify-target-frameworks)

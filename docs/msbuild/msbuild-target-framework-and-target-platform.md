---
title: MSBuild-Zielframework und -Zielplattform | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9760dbf4fd2eabb43e88e0b99858eba3e09c8fb5
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747404"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild-Zielframework und -Zielplattform
Ein Projekt kann erstellt werden, um in einem *Zielframework*, bei dem es sich um eine bestimmte Version von .NET Framework handelt, und auf einer *Zielplattform*, bei der es sich um eine bestimmte Softwarearchitektur handelt, ausgeführt zu werden.  Beispielsweise können Sie eine Anwendung für die Ausführung in .NET Framework 2.0 auf einer 32-Bit-Plattform entwickeln, die mit der 802x86-Prozessorfamilie kompatibel ist („x86“). Die Kombination von Zielframework und Zielplattform wird als *Zielkontext* bezeichnet.

## <a name="target-framework-and-profile"></a>Zielframework und -profil
 Ein Zielframework ist eine bestimmte Version von .NET Framework, die Ihr Projekt erstellt wird, führen Sie auf. Die Angabe eines Zielframeworks ist erforderlich, da es Compilerfunktionen und Assemblyverweise ermöglicht, die nur für diese Version des Frameworks gelten.

 Derzeit werden die folgenden Versionen von .NET Framework unterstützt:

- .NET Framework 2.0 (enthalten in Visual Studio 2005)

- .NET Framework 3.0 (enthalten [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])

- .NET Framework 3.5 (enthalten [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])

- The .NET Framework 4.5.2

- .NET Framework 4.6 (enthalten [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])

- .NET Framework 4.6.1

- The .NET Framework 4.6.2

- The .NET Framework 4.7

- The .NET Framework 4.7.1

Die Versionen von .NET Framework unterscheiden sich in der Liste der Assemblys, die als Verweise zur Verfügung stehen. Beispielsweise können Sie Windows Presentation Foundation (WPF)-Anwendungen nur erstellen, wenn Ihr Projekt auf die .NET Framework-Version 3.0 oder höher ausgelegt ist.

Das Zielframework wird in der `TargetFrameworkVersion`-Eigenschaft in einer Projektdatei angegeben. Sie können das Zielframework für ein Projekt ändern, indem Sie die Projekteigenschaftenseiten in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Die verfügbaren Werte für `TargetFrameworkVersion` sind `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7` und `v4.7.1`.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 Ein *Zielprofil* ist eine Teilmenge eines Zielframeworks. Beispielsweise enthält das .NET Framework 4-Clientprofil keine Verweise auf die MSBuild-Assemblys.

 Das Zielprofil wird in der `TargetFrameworkProfile`-Eigenschaft in einer Projektdatei angegeben. Sie können das Zielprofil ändern, indem Sie das Zielframeworksteuerelement in den Projekteigenschaftenseiten der IDE verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Zielplattform
 Eine *Plattform* ist eine Kombination aus Hardware und Software, die eine bestimmte Laufzeitumgebung definiert. Ein auf ein Objekt angewendeter

- `x86` steht für ein 32-Bit-Windows-Betriebssystem, das auf einem Intel 80x86-Prozessor oder einem vergleichbaren Prozessor ausgeführt wird.

- `x64` steht für ein 64-Bit-Windows-Betriebssystem, das auf einem Intel x64-Prozessor oder einem vergleichbaren Prozessor ausgeführt wird.

- `Xbox` steht für die Microsoft Xbox 360-Plattform.

Eine *Zielplattform* ist die spezielle Plattform, auf der Ihr Projekt ausgeführt werden kann. Die Zielplattform wird in der `PlatformTarget`-Buildeigenschaft in einer Projektdatei angegeben. Sie können die Zielplattform ändern, indem Sie die Projekteigenschaftenseiten oder den **Konfigurations-Manager** in der IDE verwenden.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

Eine *Zielkonfiguration* ist eine Teilmenge einer Zielplattform. `x86``Debug`-Konfiguration enthält z.B. nicht die meisten Codeoptimierungen. Die Zielkonfiguration wird in der `Configuration`-Buildeigenschaft in einer Projektdatei angegeben. Sie können die Zielkonfiguration ändern, indem Sie die Projekteigenschaftenseiten oder den **Konfigurations-Manager** verwenden.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
<PropertyGroup>

```

## <a name="see-also"></a>Siehe auch
- [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)

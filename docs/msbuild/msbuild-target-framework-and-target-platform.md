---
title: MSBuild-Zielframework und -Zielplattform | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 1628b0c5d74e642e1c52323a74bcd2279ad79436
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild-Zielframework und -Zielplattform
Ein Projekt kann erstellt werden, um in einem *Zielframework*, bei dem es sich um eine bestimmte Version von .NET Framework handelt, und auf einer *Zielplattform*, bei der es sich um eine bestimmte Softwarearchitektur handelt, ausgeführt zu werden.  Beispielsweise können Sie eine Anwendung für die Ausführung in .NET Framework 2.0 auf einer 32-Bit-Plattform entwickeln, die mit der 802x86-Prozessorfamilie kompatibel ist („x86“). Die Kombination von Zielframework und Zielplattform wird als *Zielkontext* bezeichnet.  
  
## <a name="target-framework-and-profile"></a>Zielframework und -profil  
 Ein Zielframework ist eine bestimmte Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], in der das Projekt ausgeführt werden kann. Die Angabe eines Zielframeworks ist erforderlich, da es Compilerfunktionen und Assemblyverweise ermöglicht, die nur für diese Version des Frameworks gelten.  
  
 Derzeit werden die folgenden Versionen von .NET Framework unterstützt:  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (enthalten in Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (enthalten in [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (enthalten in [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 (enthalten in Visual Studio 2010)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5 (enthalten in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.1 (enthalten in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (enthalten in [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  
  
 Die Versionen von .NET Framework unterscheiden sich in der Liste der Assemblys, die als Verweise zur Verfügung stehen. Beispielsweise können Sie Windows Presentation Foundation (WPF)-Anwendungen nur erstellen, wenn Ihr Projekt auf die .NET Framework-Version 3.0 oder höher ausgelegt ist.  
  
 Das Zielframework wird in der `TargetFrameworkVersion`-Eigenschaft in einer Projektdatei angegeben. Sie können das Zielframework für ein Projekt ändern, indem Sie die Projekteigenschaftenseiten in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Die verfügbaren Werte für `TargetFrameworkVersion` sind `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2` und `v4.6`.  
  
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
 Eine *Plattform* ist eine Kombination aus Hardware und Software, die eine bestimmte Laufzeitumgebung definiert. Beispiel:  
  
-   `x86` steht für ein 32-Bit-Windows-Betriebssystem, das auf einem Intel 80x86-Prozessor oder einem vergleichbaren Prozessor ausgeführt wird.  
  
-   `Xbox` steht für die Microsoft Xbox 360-Plattform.  
  
 Eine *Zielplattform* ist die spezielle Plattform, auf der Ihr Projekt ausgeführt werden kann. Die Zielplattform wird in der `Platform`-Buildeigenschaft in einer Projektdatei angegeben. Sie können die Zielplattform ändern, indem Sie die Projekteigenschaftenseiten oder den **Konfigurations-Manager** in der IDE verwenden.  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 Eine *Zielkonfiguration* ist eine Teilmenge einer Zielplattform. `x86``Debug`-Konfiguration enthält z.B. nicht die meisten Codeoptimierungen. Die Zielkonfiguration wird in der `Configuration`-Buildeigenschaft in einer Projektdatei angegeben. Sie können die Zielkonfiguration ändern, indem Sie die Projekteigenschaftenseiten oder den **Konfigurations-Manager** verwenden.  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von Zielversionen](../msbuild/msbuild-multitargeting-overview.md)

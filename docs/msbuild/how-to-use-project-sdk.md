---
title: 'Gewusst wie: Verweis auf MSBuild-Projekt-SDK | Microsoft-Dokumentation'
ms.custom: 
ms.date: 01/25/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: jeffkl
ms.author: jeffkl
manager: angerlic
ms.workload:
- multiple
ms.openlocfilehash: e5c12f319c8425bda8a90ace04c377b23aa76bd0
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-use-msbuild-project-sdks"></a>Gewusst wie: Verwenden von MSBuild-Projekts SDKs
Mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15.0 wurde das Konzept des „Projekt-SDK“ eingeführt, was die Verwendung von Software Development Kits vereinfacht, die das Importieren von Eigenschaften und Zielen erfordern.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```  
  
Während der Auswertung des Projekts fügt [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] implizite Importe im oberen und unteren Bereich Ihres Projekts hinzu:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>  
```  

## <a name="referencing-a-project-sdk"></a>Verweisen auf ein Projekt-SDK
 Es gibt drei Möglichkeiten, auf ein Projekt-SDK zu verweisen

1. Verwenden Sie das `Sdk`-Attribut des `<Project/>`-Elements:
    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```
    Wie oben erläutert, wird im oberen bzw. unteren Bereich des Projekts ein impliziter Import hinzugefügt.  Das Format des `Sdk`-Attributs ist `Name[/Version]`, wobei die Version optional ist.  Sie können z.B. `My.Custom.Sdk/1.2.3` festlegen.

2. Verwenden Sie das `<Sdk/>`-Element der obersten Ebene:
    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```
   Wie oben erläutert, wird im oberen bzw. unteren Bereich des Projekts ein impliziter Import hinzugefügt.  Das `Version`-Attribut ist nicht erforderlich.

3. Verwenden Sie das `<Import/>`-Element an einer beliebigen Stelle in Ihrem Projekt:
    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```
   Explizites Einbeziehen der Importe in Ihr Projekt erlaubt Ihnen die vollständige Kontrolle über die Reihenfolge.

   Bei Verwendung des `<Import/>`-Elements können Sie auch ein optionales `Version`-Attribut angeben.  Sie können z.B. `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />` festlegen.

## <a name="how-project-sdks-are-resolved"></a>Wie Projekt-SDKs gelöst werden
Beim Auswerten des Imports löst [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] den Pfad zum Projekt-SDK dynamisch basierend auf dem Namen und der Version auf, die Sie angegeben haben.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bietet auch eine Liste der registrierten SDK-Resolver, die Plug-Ins sind, die Projekt-SDKs auf Ihrem Computer suchen.  Zu diesen Plug-Ins zählen:

1. Ein NuGet-basierter Resolver, der Ihre konfigurierten Paketfeeds auf NuGet-Pakete abfragt, die der ID und Version des von Ihnen angegebenen SDK entsprechen.<br/>
   Dieser Resolver ist nur aktiv, wenn Sie eine optionale Version angegeben haben, und kann für jedes benutzerdefinierte Projekt-SDK verwendet werden.  
2. Ein .NET CLI-Resolver, der mit .NET CLI installierte SDKs auflöst.<br/>
   Dieser Resolver sucht Projekt-SDKs wie z.B. `Microsoft.NET.Sdk` und `Microsoft.NET.Sdk.Web`, die Bestandteil des Produkts sind.
3. Ein standardmäßiger Resolver, der mit MSBuild installierte SDKs auflöst.

Der NuGet-basierte SDK-Resolver unterstützt die Angabe einer Version in Ihrer [global.json](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json), mit der Sie die Projekt-SDK-Version zentral anstatt in jedem einzelnen Projekt steuern können:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```
Nur eine Version jedes Projekt-SDK kann während eines Builds verwendet werden.  Wenn Sie auf zwei unterschiedliche Versionen desselben Projekt-SDK verweisen, gibt MSBuild eine Warnung aus.  Sie sollten **keine** Version in Ihren Projekten angeben, wenn eine Version in Ihrer `global.json` angegeben ist.  

## <a name="see-also"></a>Siehe auch  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [Anpassen Ihres Builds](../msbuild/customize-your-build.md)   

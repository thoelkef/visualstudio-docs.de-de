---
title: 'Vorgehensweise: Verweisen auf ein MSBuild-Projekt-SDK | Microsoft-Dokumentation'
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d40e437763ba3eb75daa80a3a1bbf55ba9d896c9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574456"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Vorgehensweise: Verwenden von MSBuild-Projekt SDKs

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

## <a name="reference-a-project-sdk"></a>Verweisen auf ein Projekt SDK

 Es gibt drei Möglichkeiten, auf ein Projekt SDK zu verweisen:

1. Verwenden Sie das `Sdk`-Attribut des `<Project/>`-Elements:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Wie oben erläutert, wird im oberen bzw. unteren Bereich des Projekts ein impliziter Import hinzugefügt.
    
    Um eine bestimmte SDK-Version anzugeben, können Sie sie an das `Sdk`-Attribut anfügen:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Dies ist derzeit die einzige unterstützte Methode, in Visual Studio für Mac auf ein Projekt-SDK zu verweisen.

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

## <a name="how-project-sdks-are-resolved"></a>Lösen von Projekt SDKs

Beim Auswerten des Imports löst [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] den Pfad zum Projekt-SDK dynamisch basierend auf dem Namen und der Version auf, die Sie angegeben haben.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bietet auch eine Liste der registrierten SDK-Resolver, die Plug-Ins sind, die Projekt-SDKs auf Ihrem Computer suchen.  Zu diesen Plug-Ins zählen:

1. Ein NuGet-basierter Resolver, der Ihre konfigurierten Paketfeeds auf NuGet-Pakete abfragt, die der ID und Version des von Ihnen angegebenen SDK entsprechen.<br/>
   Dieser Resolver ist nur aktiv, wenn Sie eine optionale Version angegeben haben, und kann für jedes benutzerdefinierte Projekt-SDK verwendet werden.
2. Ein .NET CLI-Resolver, der mit .NET CLI installierte SDKs auflöst.<br/>
   Dieser Resolver sucht Projekt-SDKs wie z.B. `Microsoft.NET.Sdk` und `Microsoft.NET.Sdk.Web`, die Bestandteil des Produkts sind.
3. Ein standardmäßiger Resolver, der mit MSBuild installierte SDKs auflöst.

Der NuGet-basierte SDK-Resolver unterstützt die Angabe einer Version in Ihrer [global.json](/dotnet/core/tools/global-json), mit der Sie die Projekt-SDK-Version zentral anstatt in jedem einzelnen Projekt steuern können:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Nur eine Version jedes Projekt-SDK kann während eines Builds verwendet werden.  Wenn Sie auf zwei unterschiedliche Versionen desselben Projekt-SDK verweisen, gibt MSBuild eine Warnung aus.  Sie sollten **keine** Version in Ihren Projekten angeben, wenn in Ihrer *global.json*-Datei eine Version angegeben ist.

## <a name="see-also"></a>Siehe auch

- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [Customize your build (Anpassen Ihres Builds)](../msbuild/customize-your-build.md)
- [Pakete, Metadaten und Frameworks](/dotnet/core/packages)
- [Erweiterungen des CSPROJ-Formats für .NET Core](/dotnet/core/tools/csproj)

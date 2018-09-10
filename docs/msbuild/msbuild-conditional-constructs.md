---
title: Bedingte Konstrukte in MSBuild | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ade8344b5f4189e9588fc8e75ef88fa5cf8f8c5
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080196"
---
# <a name="msbuild-conditional-constructs"></a>Bedingte Konstrukte in MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stellt einen Mechanismus für Entweder/Oder-Verarbeitung mit den Elementen [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) und [Otherwise](../msbuild/otherwise-element-msbuild.md) bereit.  
  
## <a name="use-the-choose-element"></a>Verwenden des Elements „Choose“  
 Das `Choose`-Element enthält mehrere `When`-Elemente und `Condition`-Attribute, die in der Reihenfolge von oben nach unten getestet werden, bis eins `true` ergibt. Wenn mehr als ein `When`-Element `true` ergibt, wird nur das Erste verwendet. Falls ein `Otherwise`-Element vorhanden ist, wird es ausgewertet, wenn keine Bedingung für ein `When`-Element `true` ergibt.  
  
 `Choose`-Elemente können als untergeordnete Elemente der Elemente `Project`, `When` und `Otherwise` verwendet werden. Die Elemente `When` und `Otherwise` können über die untergeordneten Elemente `ItemGroup`, `PropertyGroup` und `Choose` verfügen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Elemente `Choose` und `When` für die Entweder/Oder-Verarbeitung verwendet. Die Eigenschaften und Elemente für das Projekt werden anhand des Werts der `Configuration`-Eigenschaft festgelegt.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Choose-Element (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [When-Element (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise-Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)
---
title: When-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93fd259e00d7a8f849b97cb97c3f950cd95f57ed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761541"
---
# <a name="when-element-msbuild"></a>When-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Gibt einen möglichen Codeblock an, den das `Choose`-Element auswählen kann.  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  
  
## <a name="syntax"></a>Syntax  
  
```  
<When Condition="'StringA'=='StringB'">  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</When>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Bedingung|Erforderliches Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Auswählen](../msbuild/choose-element-msbuild.md)|Optionales Element.<br /><br /> Wertet untergeordnete Elemente aus, um einen auszuführenden Codeabschnitt auszuwählen. Es kann keine oder mehrere `Choose`-Elemente in einem `When`-Element geben.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Optionales Element.<br /><br /> Enthält eine Reihe von benutzerdefinierten [Item](../msbuild/item-element-msbuild.md)-Elementen. Es kann keine oder mehrere `ItemGroup`-Elemente in einem `When`-Element geben.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Optionales Element.<br /><br /> Enthält eine Reihe von benutzerdefinierten [Eigenschaft](../msbuild/property-element-msbuild.md)-Elementen. Es kann keine oder mehrere `PropertyGroup`-Elemente in einem `When`-Element geben.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Choose-Element (MSBuild)](../msbuild/choose-element-msbuild.md)|Wertet untergeordnete Elemente aus, um einen auszuführenden Codeabschnitt auszuwählen.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn das `Condition`-Attribut TRUE ergibt, werden die untergeordneten Elemente `ItemGroup` und `PropertyGroup` des `When`-Elements ausgeführt, und alle nachfolgenden `When`-Elemente werden übersprungen.  
  
 Die Elemente `Choose`, `When` und `Otherwise` werden zusammen verwendet, um eine Möglichkeit zu bieten, einen Codeabschnitt aus einer Reihe von möglichen Alternativen zur Ausführung auszuwählen. Weitere Informationen finden Sie unter [MSBuild Conditional Constructs](../msbuild/msbuild-conditional-constructs.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Projekt verwendet das `Choose`-Element, um auszuwählen, welche Gruppe von Eigenschaftswerten in den `When`-Elementen festgelegt werden soll. Wenn die `Condition`-Attribute beider `When`-Elemente `false` ergeben, werden die Eigenschaftswerte im `Otherwise`-Element festgelegt.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
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
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
    </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md)  (Bedingte Konstrukte in MSBuild)  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md) (Referenz zum Projektdateischema von MSBuild)

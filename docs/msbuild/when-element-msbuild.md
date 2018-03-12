---
title: When-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 99da11e22b7e74feee4da4fa25b502bac563f0b2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="when-element-msbuild"></a>When-Element (MSBuild)
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

|Attribut|description|  
|---------------|-----------------|  
|Bedingung|Erforderliches Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  

### <a name="child-elements"></a>Untergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Auswählen](../msbuild/choose-element-msbuild.md)|Optionales Element.<br /><br /> Wertet untergeordnete Elemente aus, um einen auszuführenden Codeabschnitt auszuwählen. Es kann keine oder mehrere `Choose`-Elemente in einem `When`-Element geben.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Optionales Element.<br /><br /> Enthält eine Reihe von benutzerdefinierten [Item](../msbuild/item-element-msbuild.md)-Elementen. Es kann keine oder mehrere `ItemGroup`-Elemente in einem `When`-Element geben.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Optionales Element.<br /><br /> Enthält eine Reihe von benutzerdefinierten [Eigenschaft](../msbuild/property-element-msbuild.md)-Elementen. Es kann keine oder mehrere `PropertyGroup`-Elemente in einem `When`-Element geben.|  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Choose-Element (MSBuild)](../msbuild/choose-element-msbuild.md)|Wertet untergeordnete Elemente aus, um einen auszuführenden Codeabschnitt auszuwählen.|  

## <a name="remarks"></a>Hinweise  
 Wenn das `Condition`-Attribut TRUE ergibt, werden die untergeordneten Elemente `ItemGroup` und `PropertyGroup` des `When`-Elements ausgeführt, und alle nachfolgenden `When`-Elemente werden übersprungen.  

 Die Elemente `Choose`, `When` und `Otherwise` werden zusammen verwendet, um eine Möglichkeit zu bieten, einen Codeabschnitt aus einer Reihe von möglichen Alternativen zur Ausführung auszuwählen. Weitere Informationen finden Sie unter [MSBuild Conditional Constructs](../msbuild/msbuild-conditional-constructs.md).  

## <a name="example"></a>Beispiel  
 Das folgende Projekt verwendet das `Choose`-Element, um auszuwählen, welche Gruppe von Eigenschaftswerten in den `When`-Elementen festgelegt werden soll. Wenn die `Condition`-Attribute beider `When`-Elemente `false` ergeben, werden die Eigenschaftswerte im `Otherwise`-Element festgelegt.  

```xml  
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

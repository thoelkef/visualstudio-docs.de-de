---
title: Otherwise-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e0b824b8be8b3697673d0d1f09a20b6a7c1cee58
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="otherwise-element-msbuild"></a>Otherwise-Element (MSBuild)
Legt den Codeblock fest, der ausgeführt – und nur dann ausgeführt – wird, wenn die Bedingungen aller `When`-Elemente als `false` ausgewertet werden.  

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
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  
 Keine  

### <a name="child-elements"></a>Untergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Auswählen](../msbuild/choose-element-msbuild.md)|Optionales Element.<br /><br /> Wertet untergeordnete Elemente aus, um einen auszuführenden Codeabschnitt auszuwählen. Es kann keine oder mehrere `Choose`-Elemente in einem `Otherwise`-Element geben.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Optionales Element.<br /><br /> Enthält eine Reihe von benutzerdefinierten [Item](../msbuild/item-element-msbuild.md)-Elementen. Es kann keine oder mehrere `ItemGroup`-Elemente in einem `Otherwise`-Element geben.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Optionales Element.<br /><br /> Enthält eine Reihe von benutzerdefinierten [Eigenschaft](../msbuild/property-element-msbuild.md)-Elementen. Es kann keine oder mehrere `PropertyGroup`-Elemente in einem `Otherwise`-Element geben.|  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Auswählen](../msbuild/choose-element-msbuild.md)|Wertet untergeordnete Elemente aus, um einen auszuführenden Codeabschnitt auszuwählen.|  

## <a name="remarks"></a>Hinweise  
 Möglicherweise gibt es nur ein `Otherwise`-Element in einem `Choose` -Element, und es muss das letzte Element sein.  

 Die `Choose`-, `When`- und `Otherwise`-Elemente werden zusammen verwendet, um eine Möglichkeit zu bieten, einen Codeabschnitt aus einer Reihe von möglichen Alternativen zur Ausführung auszuwählen. Weitere Informationen finden Sie unter [MSBuild Conditional Constructs](../msbuild/msbuild-conditional-constructs.md).  

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

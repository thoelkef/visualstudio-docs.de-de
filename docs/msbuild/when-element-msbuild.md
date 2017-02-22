---
title: "When Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#When"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<When> Element [MSBuild]"
  - "When Element [MSBuild]"
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# When Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt einen möglichen Codeblock an, den das `Choose`\-Element auswählen kann.  
  
## Syntax  
  
```  
<When Condition="'StringA'=='StringB'">  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</When>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|Bedingung|Erforderliches Attribut.<br /><br /> Die auszuwertende Bedingung.  Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Untergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Optionales Element.<br /><br /> Wertet untergeordnete Elemente aus, um einen Codeabschnitt auszuwählen, der ausgeführt werden soll.  Es kann keine oder mehrere `Choose`\-Elemente in einem `When`\-Element geben.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Optionales Element.<br /><br /> Enthält benutzerdefinierte [Item](../msbuild/item-element-msbuild.md)\-Elemente.  Es kann keine oder mehrere `ItemGroup`\-Elemente in einem `When`\-Element geben.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Optionales Element.<br /><br /> Enthält benutzerdefinierte [Property](../msbuild/property-element-msbuild.md)\-Elemente.  Es kann keine oder mehrere `PropertyGroup`\-Elemente in einem `When`\-Element geben.|  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Choose Element \(MSBuild\)](../msbuild/choose-element-msbuild.md)|Wertet untergeordnete Elemente aus, um einen Codeabschnitt auszuwählen, der ausgeführt werden soll.|  
  
## Hinweise  
 Wenn das `Condition`\-Attribut true ergibt, werden das untergeordnete `ItemGroup`\-Element und das untergeordnete `PropertyGroup`\-Element des `When`\-Elements ausgeführt, und alle folgenden `When`\-Elemente werden übersprungen.  
  
 Das `Choose`\-Element, das `When`\-Element und das `Otherwise`\-Element werden zusammen verwendet, um die Auswahl eines auszuführenden Codeabschnitts aus verschiedenen Alternativen zu ermöglichen.  Weitere Informationen finden Sie unter [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md).  
  
## Beispiel  
 Im folgenden Projekt wird das `Choose`\-Element verwendet, um die Eigenschaftswerte in den `When`\-Elementen auszuwählen, die festgelegt werden sollen.  Wenn die `Condition`\-Attribute beider `When`\-Elemente `false` ergeben, werden die Eigenschaftswerte im `Otherwise`\-Element festgelegt.  
  
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
  
## Siehe auch  
 [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)
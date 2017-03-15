---
title: "Choose Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Choose"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Choose> Element [MSBuild]"
  - "Choose Element [MSBuild]"
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Choose Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wertet untergeordnete Elemente aus, um auszuwertende `ItemGroup`\-Elemente und\/oder `PropertyGroup`\-Elemente auszuwählen.  
  
## Syntax  
  
```  
<Choose>  
    <When Condition="'StringA'=='StringB'">... </When>  
    <Otherwise>... </Otherwise>  
</Choose>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Optionales Element.<br /><br /> Gibt den Codeblock mit `PropertyGroup`\-Elementen und `ItemGroup`\-Elementen an, die ausgewertet werden sollen, wenn die Bedingungen aller `When`\-Elemente `false` ergeben.  Ein `Choose`\-Element kann kein oder ein `Otherwise`\-Element enthalten. Dieses muss das letzte Element sein.|  
|[When](../msbuild/when-element-msbuild.md)|Erforderliches Element.<br /><br /> Gibt einen möglichen Codeblock an, den das `Choose`\-Element auswählen kann.  Es kann ein oder mehrere `When`\-Elemente in einem `Choose`\-Element geben.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Gibt den Codeblock an, der ausgeführt werden soll, wenn die Bedingungen aller `When`\-Elemente `false` ergeben.|  
|[Project](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei.|  
|[When](../msbuild/when-element-msbuild.md)|Gibt einen möglichen Codeblock an, den das `Choose`\-Element auswählen kann.|  
  
## Hinweise  
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
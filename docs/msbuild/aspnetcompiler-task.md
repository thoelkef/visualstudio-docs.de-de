---
title: "AspNetCompiler Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AspNetCompiler task"
  - "AspNetCompiler task [MSBuild]"
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AspNetCompiler Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `AspNetCompiler`\-Aufgabe umschließt aspnet\_compiler.exe, ein Hilfsprogramm, mit dem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendungen vorkompiliert werden können.  
  
## Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `AspNetCompiler`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AllowPartiallyTrustedCallers`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn dieser Parameter ist `true`, wird die Assembly mit starkem Namen teilweise vertrauenswürdige Aufrufer zulassen.|  
|`Clean`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn dieser Parameter den Wert `true` aufweist, wird die vorkompilierte Anwendung sauber erstellt.  Möglicherweise zuvor kompilierte Komponenten werden erneut kompiliert.  Der Standardwert ist `false`.  Dieser Parameter entspricht dem **\-c**\-Schalter von aspnet\_compiler.exe.|  
|`Debug`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn dieser Parameter den Wert `true` aufweist, werden während der Kompilierung Debuginformationen \(PDB\-Datei\) ausgegeben.  Der Standardwert ist `false`.  Dieser Parameter entspricht dem **\-d**\-Schalter von aspnet\_compiler.exe.|  
|`DelaySign`|Optionaler `Boolean`\-Parameter.<br /><br /> Ist dieser Parameter `true`, wird die Assembly beim Erstellen nicht vollständig signiert.|  
|`FixedNames`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn dieser Parameter ist `true`, werden den kompilierten Assemblys feste Namen gegeben..|  
|`Force`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn dieser Parameter den Wert `true` aufweist, überschreibt die Aufgabe das Zielverzeichnis, sofern dieses bereits vorhanden ist.  Bestehender Inhalt geht verloren.  Der Standardwert ist `false`.  Dieser Parameter entspricht dem **\-f**\-Schalter von aspnet\_compiler.exe.|  
|`KeyContainer`|Optionaler `String`\-Parameter.<br /><br /> Gibt einen starken Namenschlüsselcontainer an.|  
|`KeyFile`|Optionaler `String`\-Parameter.<br /><br /> Gibt den physischen Pfad zur Schlüsseldatei mit starkem Namen...|  
|`MetabasePath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den vollständigen IIS\-Metabasispfad der Anwendung an.  Dieser Parameter kann nicht mit dem `VirtualPath`\-Parameter oder dem `PhysicalPath`\-Parameter kombiniert werden.  Dieser Parameter entspricht dem **\-m**\-Schalter von aspnet\_compiler.exe.|  
|`PhysicalPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den physikalischen Pfad der Anwendung an, die kompiliert werden soll.  Wenn dieser Parameter nicht angegeben ist, wird anhand der IIS\-Metabasis nach der Anwendung gesucht.  Dieser Parameter entspricht dem **\-p**\-Schalter von aspnet\_compiler.exe.|  
|`TargetFrameworkMoniker`|Optionaler `String`\-Parameter.<br /><br /> Gibt den TargetFrameworkMoniker an, der angibt, welche .NET Framework\-Version von aspnet\_compiler.exe verwendet werden soll.  Akzeptiert nur .NET Framework\-Moniker.|  
|`TargetPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den physikalischen Pfad an, in dem die Anwendung kompiliert wird.  Ist der Pfad nicht angegeben, wird die Anwendung direkt vorkompiliert.|  
|`Updateable`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn dieser Parameter den Wert `true` aufweist, ist die vorkompilierte Anwendung aktualisierbar.  Der Standardwert ist `false`.  Dieser Parameter entspricht dem **\-u**\-Schalter von aspnet\_compiler.exe.|  
|`VirtualPath`|Optionaler `String`\-Parameter.<br /><br /> Der virtuelle Pfad der zu kompilierenden Anwendung.  Wenn `PhysicalPath` angegeben ist, wird anhand des physikalischen Pfads nach der Anwendung gesucht.  Andernfalls wird die IIS\-Metabasis verwendet und angenommen, dass sich die Anwendung im Standardverzeichnis befindet.  Dieser Parameter entspricht dem **\-v**\-Schalter von aspnet\_compiler.exe.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird die `AspNetCompiler`\-Aufgabe verwendet, um eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung vorzukompilieren.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
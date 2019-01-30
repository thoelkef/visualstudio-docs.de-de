---
title: Verwenden der AspNetCompiler-Aufgabe zum Vorkompilieren von ASP.NET-Anwendungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 992cf68dc8a8010edeb59ffb055f6a67ea48d4f8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040553"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler-Aufgabe
Die `AspNetCompiler`-Aufgabe umschließt *aspnet_compiler.exe*, ein Hilfsprogramm zum Vorkompilieren von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendungen.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `AspNetCompiler` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn dieser Parameter `true` ist, erlaubt die Assembly mit starkem Namen Aufrufer, die nicht voll vertrauenswürdig sind.|  
|`Clean`|Optionaler `Boolean`-Parameter<br /><br /> Wenn dieser Parameter `true` ist, wird die vorkompilierte Anwendung bereinigt erstellt. Zuvor kompilierte Komponenten werden erneut kompiliert. Der Standardwert ist `false`sein. Dieser Parameter entspricht dem **-c**-Schalter in *aspnet_compiler.exe*.|  
|`Debug`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn dieser Parameter `true` ist, werden während der Kompilierung Debuginformationen (PDB-Datei) ausgegeben. Der Standardwert ist `false`sein. Dieser Parameter entspricht dem **-d**-Schalter in *aspnet_compiler.exe*.|  
|`DelaySign`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn dieser Parameter `true` ist, wird die Assembly bei ihrer Erstellung nicht vollständig signiert.|  
|`FixedNames`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn dieser Parameter `true` ist, erhalten die kompilierten Assemblys feste Namen.|  
|`Force`|Optionaler `Boolean`-Parameter<br /><br /> Wenn dieser Parameter `true` ist, überschreibt die Aufgabe das Zielverzeichnis, wenn es bereits vorhanden ist. Vorhandene Inhalte gehen verloren. Der Standardwert ist `false`sein. Dieser Parameter entspricht dem **-f**-Schalter in *aspnet_compiler.exe*.|  
|`KeyContainer`|Optionaler `String` -Parameter.<br /><br /> Gibt einen Schlüsselcontainer mit starkem Namen an.|  
|`KeyFile`|Optionaler `String` -Parameter.<br /><br /> Legt den physischen Pfad zur Schlüsseldatei mit starkem Namen fest.|  
|`MetabasePath`|Optionaler `String` -Parameter.<br /><br /> Legt den vollständigen IIS-Metabasispfad der Anwendung fest. Dieser Parameter kann nicht mit Parameter `VirtualPath` oder `PhysicalPath` kombiniert werden. Dieser Parameter entspricht dem **-m**-Schalter in *aspnet_compiler.exe*.|  
|`PhysicalPath`|Optionaler `String` -Parameter.<br /><br /> Legt den physischen Pfad der zu kompilierenden Anwendung fest. Wenn dieser Parameter nicht vorhanden ist, wird die IIS-Metabasis verwendet, um die Anwendung zu suchen. Dieser Parameter entspricht dem **-p**-Schalter in *aspnet_compiler.exe*.|  
|`TargetFrameworkMoniker`|Optionaler `String` -Parameter.<br /><br /> Legt den TargetFrameworkMoniker fest, der angibt, welche .NET Framework-Version von *aspnet_compiler.exe* verwendet werden soll. Akzeptiert nur .NET Framework-Moniker.|  
|`TargetPath`|Optionaler `String` -Parameter.<br /><br /> Legt den physischen Pfad fest, unter dem die Anwendung kompiliert wird. Wenn nicht angegeben, wird die Anwendung direkt vorkompiliert.|  
|`Updateable`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn dieser Parameter `true` ist, ist die vorkompilierte Anwendung aktualisierbar.  Der Standardwert ist `false`sein. Dieser Parameter entspricht dem **-u**-Schalter in *aspnet_compiler.exe*.|  
|`VirtualPath`|Optionaler `String` -Parameter.<br /><br /> Der virtuelle Pfad der zu kompilierenden Anwendung. Wenn `PhysicalPath` festgelegt ist, wird der physische Pfad verwendet, um die Anwendung zu suchen. Andernfalls wird die IIS-Metabasis verwendet, und es wird angenommen, dass sich die Anwendung am Standardspeicherort befindet. Dieser Parameter entspricht dem **-v**-Schalter in *aspnet_compiler.exe*.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die `AspNetCompiler`-Aufgabe zum Vorkompilieren einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung verwendet.  
  
```xml  
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
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)

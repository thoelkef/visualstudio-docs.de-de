---
title: SGen-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4ebb6579cd4ac4ee96547bbc7d70f471f17e4e53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sgen-task"></a>SGen-Aufgabe
Erstellt eine XML-Serialisierungsassembly für Typen in der angegebenen Assembly. Diese Aufgabe umschließt das XML Serializer Generator-Tool (Sgen.exe). Weitere Informationen finden Sie unter [XML Serializer Generator-Tool (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `SGen` -Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|`BuildAssemblyName`|Erforderlicher `String` -Parameter.<br /><br /> Die Assembly, für die Serialisierungscode generiert werden soll.|  
|`BuildAssemblyPath`|Erforderlicher `String` -Parameter.<br /><br /> Der Pfad der Assembly, für die Serialisierungscode generiert werden soll.|  
|`DelaySign`|Optionaler `Boolean` -Parameter.<br /><br /> Ist der Wert `true`, gibt dies an, dass die Assembly vollständig signiert werden soll. Ist der Wert `false`, gibt dies an, dass Sie nur den öffentlichen Schlüssel in die Assembly platzieren möchten.<br /><br /> Dieser Parameter hat nur dann Auswirkungen, wenn Sie ihn entweder mit dem `KeyFile`- oder `KeyContainer`-Parameter verwenden.|  
|`KeyContainer`|Optionaler `String` -Parameter.<br /><br /> Gibt einen Container an, der ein Schlüsselpaar enthält. Dieser wird zum Signieren der Assembly verwendet, indem ein öffentlicher Schlüssel in das Assemblymanifest eingefügt wird. Dann wird die endgültige Assembly von der Aufgabe mit dem privaten Schlüssel signiert.|  
|`KeyFile`|Optionaler `String` -Parameter.<br /><br /> Gibt ein Schlüsselpaar oder einen öffentlichen Schlüssel an, das bzw. der zum Signieren einer Assembly verwendet werden soll. Der Compiler fügt den öffentlichen Schlüssel in das Assemblymanifest ein und signiert anschließend die endgültige Assembly mit dem privaten Schlüssel.|  
|`Platform`|Optionaler `String` -Parameter.<br /><br /> Ruft die Compiler-Plattform ab, die zum Generieren der Ausgabeassembly verwendet wird, oder legt sie fest. Dieser Parameter kann den Wert `x86`, `x64` oder `anycpu` haben. Der Standardwert ist `anycpu`.|  
|`References`|Optionaler `String[]` -Parameter.<br /><br /> Gibt die Assemblys an, auf die von den Typen, die XML-Serialisierung erfordern, verwiesen wird.|  
|`SdkToolsPath`|Optionaler `String` -Parameter.<br /><br /> Legt den Pfad zu den SDK-Tools wie z.B. „resgen.exe“ fest.|  
|`SerializationAssembly`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die generierte Serialisierungsassembly.|  
|`SerializationAssemblyName`|Optionaler `String` -Parameter.<br /><br /> Gibt den Namen der generierten Serialisierungsassembly an.|  
|`ShouldGenerateSerializer`|Erforderlicher `Boolean` -Parameter.<br /><br /> Wenn `true`, sollte die SGen-Aufgabe eine Serialisierungsassembly generieren.|  
|`Timeout`|Optionaler `Int32` -Parameter.<br /><br /> Gibt die Zeitdauer in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird. Der Standardwert ist `Int.MaxValue`. Dieser gibt an, dass es kein Zeitlimit gibt.|  
|`ToolPath`|Optionaler `String` -Parameter.<br /><br /> Legt den Speicherort fest, von wo aus die Aufgabe die zugrunde liegende ausführbare Datei (sgen.exe) lädt. Wenn dieser Parameter nicht angegeben ist, verwendet die Aufgabe den SDK-Installationspfad, der der Version des Frameworks entspricht, das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ausführt.|  
|`Types`|Optionaler `String[]` -Parameter.<br /><br /> Ruft eine Liste der spezifischen Typen ab, für die Serialisierungscode generiert werden soll, oder legt sie fest. SGen generiert nur für diese Typen Serialisierungscode.|  
|`UseProxyTypes`|Erforderlicher `Boolean` -Parameter.<br /><br /> Wenn `true`, generiert die SGen-Aufgabe Serialisierungscode ausschließlich für die Proxytypen des XML-Webdiensts.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)  (MSBuild-Aufgabenreferenz)  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
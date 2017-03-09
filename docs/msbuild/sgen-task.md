---
title: "SGen Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#SGen"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "SGen task [MSBuild]"
  - "MSBuild, SGen task"
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SGen Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt eine XML\-Serialisierungsassembly für Typen in der angegebenen Assembly.  Diese Aufgabe umschließt das XML Serializer Generator\-Tool \(Sgen.exe\).  Weitere Informationen finden Sie unter [XML Serializer Generator\-Tool \(Sgen.exe\)](../Topic/XML%20Serializer%20Generator%20Tool%20\(Sgen.exe\).md).  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `SGen`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`BuildAssemblyName`|Erforderlicher `String`\-Parameter.<br /><br /> Die Assembly, für die Serialisierungscode generiert werden soll.|  
|`BuildAssemblyPath`|Erforderlicher `String`\-Parameter.<br /><br /> Der Pfad zur Assembly, für die Serialisierungscode generiert werden soll.|  
|`DelaySign`|Optionaler `Boolean`\-Parameter.<br /><br /> Der Wert `true` gibt an, dass die Assembly vollständig signiert werden soll.  Der Wert `false` gibt an, dass Sie nur den öffentlichen Schlüssel in die Assembly einfügen möchten.<br /><br /> Dieser Parameter hat nur Auswirkungen, wenn er mit dem `KeyFile`\-Parameter oder dem `KeyContainer`\-Parameter verwendet wird.|  
|`KeyContainer`|Optionaler `String`\-Parameter.<br /><br /> Gibt einen Container an, der ein Schlüsselpaar enthält.  Die Assembly wird signiert, indem ein öffentlicher Schlüssel in das Assemblymanifest eingefügt wird.  Die Aufgabe signiert dann die endgültige Assembly mit dem privaten Schlüssel.|  
|`KeyFile`|Optionaler `String`\-Parameter.<br /><br /> Gibt ein Schlüsselpaar oder einen öffentlichen Schlüssel an, um damit eine Assembly zu signieren.  Der Compiler fügt den öffentlichen Schlüssel in das Assemblymanifest ein und signiert anschließend die endgültige Assembly mit dem privaten Schlüssel.|  
|`Platform`|Optionaler `String`\-Parameter.<br /><br /> Ruft die Compiler\-Plattform ab oder legt diese fest, die zum Generieren der Ausgabeassembly verwendet wird.  Dieser Parameter kann den Wert `x86`, `x64` oder `anycpu` aufweisen.  Der Standardwert ist `anycpu`.|  
|`References`|Optionaler `String[]`\-Parameter.<br /><br /> Gibt die Assemblys an, auf die von den Typen, die XML\-Serialisierung erfordern, verwiesen wird.|  
|`SdkToolsPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Pfad zu den SDK\-Tools, wie z. B. resgen.exe an.|  
|`SerializationAssembly`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die generierte Serialisierungsassembly.|  
|`SerializationAssemblyName`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Namen der generierten Serialisierungsassembly an.|  
|`ShouldGenerateSerializer`|Erforderlicher `Boolean`\-Parameter.<br /><br /> Bei `true` generiert die SGen\-Aufgabe eine Serialisierungsassembly.|  
|`Timeout`|Optionaler `Int32`\-Parameter.<br /><br /> Gibt die Zeit in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird.  Der Standardwert lautet `Int.MaxValue`. Dieser gibt an, dass kein Timeoutintervall festgelegt ist.|  
|`ToolPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Speicherort an, von dem die Aufgabe die zugrunde liegende ausführbare Datei \(sgen.exe\) lädt.  Wird dieser Parameter nicht angegeben, verwendet die Aufgabe den SDK\-Installationspfad für die Framework\-Version, in der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ausgeführt wird.|  
|`Types`|Optionaler `String[]`\-Parameter.<br /><br /> Ruft eine Liste der spezifischen Typen zum Generieren des die Serialisierungscodes ab oder legt diese fest.  SGen generiert Serialisierungscode nur für diese Typen.|  
|`UseProxyTypes`|Erforderlicher `Boolean`\-Parameter.<br /><br /> Beim Wert `true` generiert die SGen\-Aufgabe nur Serialisierungscode für die Proxytypen des XML\-Webdiensts.|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)
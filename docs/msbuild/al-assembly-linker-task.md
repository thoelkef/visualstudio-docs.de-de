---
title: "AL (Assembly Linker) Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AL"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AL task [MSBuild]"
  - "MSBuild, AL task"
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AL (Assembly Linker) Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die AL\-Aufgabe umschließt AL.exe, ein Tool, das mit [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] verteilt wird.  Mit diesem Assembly Linker\-Tool wird aus einer oder mehreren Dateien, bei denen es sich um Module oder Ressourcendateien handelt, eine Assembly mit einem Manifest erstellt.  Da Compiler und Entwicklungsumgebungen diese Funktionen u. U. bereits zur Verfügung stellen, ist es häufig nicht erforderlich, diese Aufgabe direkt zu verwenden.  Das Assembly Linker\-Tool ist besonders hilfreich für Entwickler, die eine einzige Assembly aus mehreren Komponentendateien erstellen müssen, beispielsweise solche, die aus verschiedenen Sprachen zusammengestellt werden.  Mit dieser Aufgabe werden die Module nicht zu einer einzigen Assemblydatei zusammengefasst, sondern die einzelnen Module müssen verteilt werden und verfügbar sein, damit die sich ergebende Assembly korrekt geladen werden kann.  Weitere Informationen zu AL.exe finden Sie unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `AL`\-Aufgabe beschrieben.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`AlgorithmID`|Optionaler `String`\-Parameter.<br /><br /> Legt einen Algorithmus zum Hashen aller Dateien in einer Mehrfachdateiassembly mit Ausnahme der Datei, die das Assemblymanifest enthält, fest.  Weitere Informationen finden Sie in der Dokumentation zur `/algid`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`BaseAddress`|Optionaler `String`\-Parameter.<br /><br /> Legt die Adresse fest, an der eine DLL zur Laufzeit auf den Computer des Benutzers geladen wird.  Das Laden von Anwendungen kann beschleunigt werden, wenn nicht das Betriebssystem die DLLs im Prozessbereich verschiebt, sondern die Basisadresse der DLLs angegeben wird.  Dieser Parameter entspricht der \/base\[address\]\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`CompanyName`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `Company`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/comp[any]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Configuration`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `Configuration`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/config[uration]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Copyright`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `Copyright`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/copy[right]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Culture`|Optionaler `String`\-Parameter.<br /><br /> Legt die Kulturzeichenfolge fest, die mit der Assembly zu verknüpfen ist.  Weitere Informationen finden Sie in der Dokumentation zur `/c[ulture]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`DelaySign`|Optionaler `Boolean`\-Parameter.<br /><br /> `true`, wenn nur der öffentliche Schlüssel in die Assembly eingefügt werden soll; `false`, wenn die Assembly vollständig signiert werden soll.  Weitere Informationen finden Sie in der Dokumentation zur `/delay[sign]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Description`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `Description`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/descr[iption]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`EmbedResources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Bettet die angegebenen Ressourcen in das Bild ein, das das Assemblymanifest enthält.  Mit dieser Aufgabe wird der Inhalt der Ressourcendatei in das Bild kopiert.  An die an diesen Parameter übergebenen Elemente sind möglicherweise optionale Metadaten mit den Namen `LogicalName` und `Access` angefügt.  Die `LogicalName`\-Metadaten werden verwendet, um den internen Bezeichner für die Ressource anzugeben.  Die `Access`\-Metadaten können auf `private` festgelegt werden, damit die Ressource für andere Assemblys nicht sichtbar ist.  Weitere Informationen finden Sie in der Dokumentation zur `/embed[resource]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`EvidenceFile`|Optionaler `String`\-Parameter.<br /><br /> Bettet die angegebene Datei in die Assembly mit dem Ressourcennamen `Security.Evidence` ein.<br /><br /> Sie können `Security.Evidence` nicht für reguläre Ressourcen verwenden.  Dieser Parameter entspricht der `/e[vidence]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ExitCode`|Optionaler schreibgeschützter `Int32`\-Ausgabeparameter.<br /><br /> Gibt den vom ausgeführten Befehl bereitgestellten Exitcode an.|  
|`FileVersion`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `File Version`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/fileversion`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Flags`|Optionaler `String`\-Parameter.<br /><br /> Legt einen Wert für das `Flags`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/flags`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`GenerateFullPaths`|Optionaler `Boolean`\-Parameter.<br /><br /> Veranlasst die Aufgabe, den absoluten Pfad für alle Dateien zu verwenden, die in einer Fehlermeldung gemeldet werden.  Dieser Parameter entspricht der `/fullpaths`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`KeyContainer`|Optionaler `String`\-Parameter.<br /><br /> Gibt einen Container an, der ein Schlüsselpaar enthält.  Dieser wird zum Signieren der Assembly \(d. h. zum Zuweisen eines starken Namens zur Assembly\) verwendet, indem ein öffentlicher Schlüssel in das Assemblymanifest eingefügt wird.  Die Aufgabe signiert dann die endgültige Assembly mit dem privaten Schlüssel.  Weitere Informationen finden Sie in der Dokumentation zur `/keyn[ame]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`KeyFile`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Datei fest, die ein Schlüsselpaar oder einfach einen öffentlichen Schlüssel zum Signieren einer Assembly enthält.  Der Compiler fügt den öffentlichen Schlüssel in das Assemblymanifest ein und signiert anschließend die endgültige Assembly mit dem privaten Schlüssel.  Weitere Informationen finden Sie in der Dokumentation zur `/keyf[ile]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`LinkResources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Verknüpft die angegebenen Ressourcendateien mit einer Assembly.  Die Ressource wird Teil der Assembly, die Datei wird jedoch nicht kopiert.  An die an diesen Parameter übergebenen Elemente sind möglicherweise optionale Metadaten mit den Namen `LogicalName`, `Target` und `Access` angefügt.  Die `LogicalName`\-Metadaten werden verwendet, um den internen Bezeichner für die Ressource anzugeben.  In den `Target`\-Metadaten können der Pfad, in den die Datei kopiert wird, und der Dateiname angegeben werden. Diese neue Datei wird dann in die Assembly kompiliert.  Die `Access`\-Metadaten können auf `private` festgelegt werden, damit die Ressource für andere Assemblys nicht sichtbar ist.  Weitere Informationen finden Sie in der Dokumentation zur `/link[resource]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`MainEntryPoint`|Optionaler `String`\-Parameter.<br /><br /> Legt den vollqualifizierten Namen \(*class.method*\) der Methode fest, die als Einstiegspunkt zu verwenden ist, wenn ein Modul in eine ausführbare Datei konvertiert wird.  Dieser Parameter entspricht der `/main`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`OutputAssembly`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>\-Ausgabeparameter.<br /><br /> Gibt den Namen der von dieser Aufgabe generierten Datei an.  Dieser Parameter entspricht der `/out`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Platform`|Optionaler `String`\-Parameter.<br /><br /> Beschränkt die Ausführbarkeit dieses Codes auf eine der folgenden Plattformen: `x86`, `Itanium`, `x64` oder `anycpu`.  Der Standardwert ist `anycpu`.  Dieser Parameter entspricht der `/platform`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ProductName`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `Product`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/prod[uct]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ProductVersion`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `ProductVersion`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/productv[ersion]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ResponseFiles`|Optionaler `String[]`\-Parameter.<br /><br /> Gibt die Antwortdateien an, die zusätzliche Optionen enthalten, die an den Assemblylinker übergeben werden sollen.|  
|`SdkToolsPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Pfad zu den SDK\-Tools, wie z. B. resgen.exe an.|  
|`SourceModules`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Ein oder mehrere Module, die in eine Assembly kompiliert werden sollen.  Die Module werden im Manifest der sich ergebenden Assembly aufgelistet. Sie müssen verteilt werden und verfügbar sein, damit die Assembly geladen werden kann.  Die an diesen Parameter übergebenen Elemente verfügen möglicherweise über zusätzliche Metadaten mit dem Namen`Target`, in denen der Pfad, in den die Datei kopiert wird, und der Dateiname angegeben werden. Diese neue Datei wird dann in die Assembly kompiliert.  Weitere Informationen finden Sie in der Dokumentation zu [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  Dieser Parameter entspricht der Liste der Module, die ohne einen bestimmten Schalter an AL.exe übergeben werden.|  
|`TargetType`|Optionaler `String`\-Parameter.<br /><br /> Legt das Dateiformat der Ausgabedatei fest: `library` \(Codebibliothek\), `exe` \(Konsolenanwendung\) oder `win` \(Windows\-basierte Anwendung\).  Der Standardwert ist `library`.  Dieser Parameter entspricht der `/t[arget]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`TemplateFile`|Optionaler `String`\-Parameter.<br /><br /> Legt die Assembly fest, von der mit Ausnahme des Kulturfelds alle Assemblymetadaten geerbt werden.  Die angegebene Assembly muss über einen starken Namen verfügen.<br /><br /> Eine Assembly, die Sie mit dem `TemplateFile`\-Parameter erstellen, ist eine Satellitenassembly.  Dieser Parameter entspricht der `/template`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Timeout`|Optionaler `Int32`\-Parameter.<br /><br /> Gibt die Zeit in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird.  Der Standardwert lautet `Int.MaxValue`. Dieser gibt an, dass kein Timeoutintervall festgelegt ist.|  
|`Title`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `Title`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/title`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ToolPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Speicherort an, von dem die Aufgabe die zugrunde liegende ausführbare Datei \(AL.exe\) lädt.  Wird dieser Parameter nicht angegeben, verwendet die Aufgabe den SDK\-Installationspfad für die Framework\-Version, in der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ausgeführt wird.|  
|`Trademark`|Optionaler `String`\-Parameter.<br /><br /> Legt eine Zeichenfolge für das `Trademark`\-Feld in der Assembly fest.  Weitere Informationen finden Sie in der Dokumentation zur `/trade[mark]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Version`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Versionsdaten für diese Assembly an.  Das Format der Zeichenfolge ist *major.minor.build.revision*.  Der Standardwert ist 0.  Weitere Informationen finden Sie in der Dokumentation zur `/v[ersion]`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Win32Icon`|Optionaler `String`\-Parameter.<br /><br /> Fügt eine ICO\-Datei in eine Assembly ein.  Die ICO\-Datei gibt der Ausgabedatei die gewünschte Darstellung im Datei\-Explorer.  Dieser Parameter entspricht der `/win32icon`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Win32Resource`|Optionaler `String`\-Parameter.<br /><br /> Fügt eine Win32\-Ressource \(RES\-Datei\) in die Ausgabedatei ein.  Weitere Informationen finden Sie in der Dokumentation zur `/win32res`\-Option unter [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird eine Assembly mit den angegebenen Optionen erstellt.  
  
```  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)
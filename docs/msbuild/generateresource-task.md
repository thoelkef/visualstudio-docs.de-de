---
title: "GenerateResource Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GenerateResource task"
  - "GenerateResource task [MSBuild]"
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateResource Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Konvertiert TXT\-Dateien und RESX\-Dateien \(XML\-basiertes Ressourcenformat\) in binäre RESOURCES\-Dateien der Common Language Runtime, die in eine ausführbare Binärdatei der Laufzeit eingebettet oder in Satellitenassemblys kompiliert werden können, oder führt den umgekehrten Vorgang aus.  Diese Aufgabe wird i. d. R. verwendet, um TXT\-Dateien oder RESX\-Dateien in RESOURCES\-Dateien zu konvertieren.  Die `GenerateResource`\-Aufgabe ist funktional mit [resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) zu vergleichen.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `GenerateResource`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`AdditionalInputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` \-Parameter.<br /><br /> Enthält zusätzliche Eingaben für die Abhängigkeitsprüfung, die durchgeführt wird von dieser Aufgabe.  Die Projekt\- und Zieldateien sollten beispielsweise Eingaben sein, um sicherzustellen, dass bei ihrer Aktualisierung sämtliche Ressourcen neu generiert werden.|  
|`EnvironmentVariables`|Optionaler `String[]`\-Parameter.<br /><br /> Gibt ein Array von Name\-Wert\-Paaren von Umgebungsvariablen an, die an die erzeugte Datei resgen.exe übergeben werden sollen, zusätzlich zum regulären Umgebungsblock \(oder diesen selektiv überschreibend\).|  
|`ExcludedInputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` \-Parameter.<br /><br /> Gibt ein Array von Elementen an, die Pfade angeben, bei denen verfolgte Eingaben bei der Aktualitätsüberprüfung ignoriert werden.|  
|`ExecuteAsTool`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, werden tlbimp.exe und aximp.exe vom entsprechenden Ziel\-Framework\-Out\-of\-Proc ausgeführt, um die erforderlichen Wrapperassemblys zu generieren.  Dieser Parameter ermöglicht Festlegung von Zielversionen von `ResolveComReferences`.|  
|`FilesWritten`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Namen aller auf den Datenträger geschriebenen Dateien.  Hierzu zählt auch die Cachedatei, sofern vorhanden.  Dieser Parameter ist für Implementierungen von Clean nützlich.|  
|`MinimalRebuildFromTracking`|Optionaler `Boolean`\-Parameter.<br /><br /> Ruft einen Schalter ab, der angibt, ob der verfolgte inkrementelle Build verwendet wird, oder legt ihn fest.  Beim Wert `true` wird der inkrementelle Build aktiviert, andernfalls wird ein erneuter Build erzwungen.|  
|`NeverLockTypeAssemblies`|Optionaler `Boolean`\-Parameter.<br /><br /> Gibt den Namen der generierten Dateien an, z. B. der RESOURCES\-Dateien.  Wenn Sie keinen Namen angeben, wird der Name der entsprechenden Eingabedatei verwendet, und die neu erstellte RESOURCES\-Datei wird in dem Verzeichnis gespeichert, in dem sich auch die Eingabedatei befindet.|  
|`OutputResources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt den Namen der generierten Dateien an, z. B. der RESOURCES\-Dateien.  Wenn Sie keinen Namen angeben, wird der Name der entsprechenden Eingabedatei verwendet, und die neu erstellte RESOURCES\-Datei wird in dem Verzeichnis gespeichert, in dem sich auch die Eingabedatei befindet.|  
|`PublicClass`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird eine stark typisierte Ressourcenklasse als öffentliche Klasse erstellt.|  
|`References`|Optionaler `String[]`\-Parameter.<br /><br /> Verweise auf Assemblys, aus denen Typen für RESX\-Dateien geladen werden sollen.  Datenelemente in RESX\-Dateien weisen u. U. den .NET\-Typ auf.  Wenn die RESX\-Datei gelesen wird, muss dieser aufgelöst werden.  Normalerweise kann die Auflösung erfolgreich mit Standardregeln für das Laden von Typen erfolgen.  Wenn Sie in `References` Assemblys bereitstellen, haben diese Vorrang.<br /><br /> Dieser Parameter ist für Ressourcen mit starker Typisierung nicht erforderlich.|  
|`SdkToolsPath`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Pfad zu den SDK\-Tools, wie z. B. resgen.exe an.|  
|`Sources`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die zu konvertierenden Elemente an.  An diesen Parameter übergebene Elemente müssen eine der folgenden Dateierweiterungen aufweisen:<br /><br /> -   `.txt`: Gibt die Erweiterung einer zu konvertierenden Textdatei an.  Textdateien dürfen nur Zeichenfolgenressourcen enthalten.<br />-   `.resx`: Gibt die Erweiterung einer zu konvertierenden XML\-basierten Ressourcendatei an.<br />-   `.restext`: Gibt das gleiche Format an wie .txt.  Diese andere Erweiterung ist nützlich, wenn Sie im Buildprozess Quelldateien, die Ressourcen enthalten, eindeutig von anderen Quelldateien differenzieren möchten.<br />-   `.resources`: Gibt die Erweiterung einer zu konvertierenden Ressourcendatei an.|  
|`StateFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt den Pfad einer optionalen Cachedatei an, die verwendet wird, um die Abhängigkeitsprüfung von Links in RESX\-Eingabedateien zu beschleunigen.|  
|`StronglyTypedClassName`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Klassennamen für die Ressourcenklasse mit starker Typisierung an.  Wenn dieser Parameter nicht angegeben wird, wird der Basisname der Ressourcendatei verwendet.|  
|`StronglyTypedFilename`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt den Dateinamen der Quelldatei an.  Wenn dieser Parameter nicht angegeben wird, wird der Name der Klasse als Basisdateiname verwendet und eine der Sprache entsprechende Erweiterung angefügt.  Beispiel: `MyClass.cs`.|  
|`StronglyTypedLanguage`|Optionaler `String`\-Parameter.<br /><br /> Gibt die Sprache an, die beim Generieren der Klassenquelle für die Ressource mit starker Typisierung verwendet werden soll.  Dieser Parameter muss genau mit einer der Sprachen übereinstimmen, die von CodeDomProvider verwendet werden.  Beispielsweise `VB` oder `C#`.<br /><br /> Wenn ein Wert an diesen Parameter übergeben wird, wird die Aufgabe angewiesen, Ressourcen mit starker Typisierung zu generieren.|  
|`StronglyTypedManifestPrefix`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Ressourcennamespace oder das Manifestpräfix an, die in der generierten Klassenquelle für die Ressource mit starker Typisierung verwendet werden sollen.|  
|`StronglyTypedNamespace`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Namespace an, der für die generierte Klassenquelle für die Ressource mit starker Typisierung verwendet werden soll.  Wenn dieser Parameter nicht angegeben wird, befinden sich alle Ressourcen mit starker Typisierung im globalen Namespace.|  
|`TLogReadFiles`|Optionaler schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Ruft ein Array von Elementen ab, die die Lesenachverfolgungsprotokolle darstellen.|  
|`TLogWriteFiles`|Optionaler schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Ruft ein Array von Elementen ab, die die Schreibnachverfolgungsprotokolle darstellen.|  
|`ToolArchitecture`|Optionaler [String](assetId:///String?qualifyHint=False&autoUpgrade=True)\-Parameter.<br /><br /> Bestimmt, ob Tracker.exe zum Erzeugen von ResGen.exe\-Prozessen verwendet werden muss.<br /><br /> Muss von einem Member der Enumeration <xref:Microsoft.Build.Utilities.ExecutableType> analysiert werden können.  Wenn `String.Empty`, wird eine Heuristik verwendet, um eine Standard\-Architektur zu bestimmen.  Muss von einem Member der Enumeration Microsoft.Build.Utilities.ExecutableType analysiert werden können.|  
|`TrackerFrameworkPath`|Optionaler assetId:///String?qualifyHint=False&autoUpgrade=True\-Parameter.<br /><br /> Gibt den Pfad zum entsprechenden .NET Framework\-Speicherort an, unter dem sich FileTracker.dll befindet.<br /><br /> Wenn festgelegt, der nimmt der Benutzer Verantwortung dafür, sicherzustellen, dass die Bitness der FileTracker.dll, die er übergibt, mit der Bitness der ResGen.exe übereinstimmt, die er verwenden möchten.  Wenn nicht festgelegt, entscheidet die Aufgabe über die richtige Stelle auf der Grundlage der aktuellen .NET Framework\-Version.|  
|`TrackerLogDirectory`|Optionaler assetId:///String?qualifyHint=False&autoUpgrade=True\-Parameter.<br /><br /> Gibt das Zwischenverzeichnis an, in dem die Nachverfolgungsprotokolle vom Ausführen dieser Aufgabe gespeichert werden.|  
|`TrackerSdkPath`|Optionaler assetId:///String?qualifyHint=False&autoUpgrade=True\-Parameter.<br /><br /> Gibt den Pfad zum entsprechenden Windows SDK\-Speicherort an, an dem sich Tracker.exe befindet.<br /><br /> Wenn festgelegt, der nimmt der Benutzer Verantwortung dafür, sicherzustellen, dass die Bitness der Tracker.exe, die er übergibt, mit der Bitness der ResGen.exe übereinstimmt, die er verwenden möchten.  Wenn nicht festgelegt, entscheidet die Aufgabe über die richtige Stelle auf der Grundlage des aktuellen Windows\-SDK.|  
|`TrackFileAccess`|Optionaler [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True)\-Parameter.<br /><br /> Bei true wird das Verzeichnis der Eingabedatei für die Auflösung relativer Pfade verwendet.|  
|`UseSourcePath`|Optionaler `Boolean`\-Parameter.<br /><br /> Der Wert `true` gibt an, dass das Verzeichnis der Eingabedatei zum Auflösen relativer Dateipfade verwendet wird.|  
  
## Hinweise  
 Da RESX\-Dateien möglicherweise Links zu anderen Ressourcendateien enthalten, genügt es nicht, einfach die Timestamps von RESX\-Dateien und RESOURCES\-Dateien zu vergleichen, um festzustellen, ob die Ausgaben aktuell sind.  Stattdessen folgt die `GenerateResource`\-Aufgabe den Links in den RESX\-Dateien und prüft auch die Timestamps der verknüpften Dateien.  Aus diesem Grund sollten Sie generell nicht das `Inputs`\-Attribut und das `Outputs`\-Attribut für das Ziel verwenden, das die `GenerateResource`\-Aufgabe enthält, da dies dazu führen kann, dass die Aufgabe übersprungen wird, wenn sie eigentlich ausgeführt werden soll.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
 Wenn Sie MSBuild 4.0 zum Abzielen auf .NET 3.5\-Projekte verwenden, schlägt der Build möglicherweise fehl für x86\-Ressourcen.  Um dieses Problem zu umgehen, können Sie das Ziel als eine AnyCPU\-Assembly erstellen.  
  
## Beispiel  
 Im folgenden Beispiel wird die `GenerateResource`\-Aufgabe verwendet, um RESOURCES\-Dateien aus den von der `Resx`\-Elementauflistung angegebenen Dateien zu generieren.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 Die `GenerateResource`\-Aufgabe verwendet die \<LogicalName\>\-Metadaten eines \<EmbeddedResource\>\-Elements, um die Ressource zu benennen, die in eine Assembly eingebettet ist.  
  
 Angenommen, dass die Assembly "myAssembly" genannt wird, wird im folgenden Code eine eingebettete Ressource mit dem Namen "someQualifier.someResource.resources" generiert:  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Ohne die \<LogicalName\>\-Metadaten wird die Ressource mit "myAssembly.myResource.resources" benannt.  Dieses Beispiel gilt nur für den Visual Basic\- und den Visual C\#\-Buildprozess.  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
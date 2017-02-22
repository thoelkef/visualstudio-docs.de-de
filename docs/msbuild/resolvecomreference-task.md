---
title: "ResolveComReference Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveCOMReference task"
  - "ResolveCOMReference task [MSBuild]"
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveComReference Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt eine Liste mit mindestens einem Typbibliotheknamen oder mindestens einer TLB\-Datei und löst die Typbibliotheken in Speicherorten auf dem Datenträger auf.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `ResolveCOMReference`\-Aufgabe beschrieben.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`DelaySign`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, fügt die Aufgabe den öffentlichen Schlüssel in die Assembly ein.  Lautet der Wert `false`, signiert die Aufgabe die Assembly vollständig.|  
|`EnvironmentVariables`|Optionaler `String[]`\-Parameter.<br /><br /> Array von Paaren von Umgebungsvariablen, durch Gleichheitszeichen getrennt.  Diese Variablen werden an die erzeugte tlbimp.exe und aximp.exe übergeben, neben dem regulären Umgebungsblock oder diesen selektiv überschreibend.|  
|`ExecuteAsTool`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, werden tlbimp.exe und aximp.exe vom entsprechenden Ziel\-Framework\-Out\-of\-Proc ausgeführt, um die erforderlichen Wrapperassemblys zu generieren.  Dieser Parameter ermöglicht Festlegung von Zielversionen.|  
|`IncludeVersionInInteropName`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird die Typelib\-Version in den Wrappernamen aufgenommen.  Der Standardwert ist `false`.|  
|`KeyContainer`|Optionaler `String`\-Parameter.<br /><br /> Gibt einen Behälter mit einem Paar aus öffentlichem und privatem<br /><br /> Schlüsselpaar.|  
|`KeyFile`|Optionaler `String`\-Parameter.<br /><br /> Gibt ein Element mit einem Paar aus öffentlichem und privatem<br /><br /> Schlüsselpaar.|  
|`NoClassMembers`|Optionaler `Boolean`\-Parameter.|  
|`ResolvedAssemblyReferences`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt die aufgelösten Assemblyverweise an.|  
|`ResolvedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt die vollqualifizierten Dateien auf dem Datenträger an, die mit den physikalischen Speicherorten der Typbibliotheken übereinstimmen, die bei dieser Aufgabe eingegeben wurden.|  
|`ResolvedModules`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.|  
|`SdkToolsPath`|Optionaler [String](assetId:///String?qualifyHint=False&autoUpgrade=True)\-Parameter.<br /><br /> Wenn `ExecuteAsTool` gleich `true` ist, muss dieser Paramete auf den Pfad der SDK\-Tools für die Zielframeworkversion festgelegt werden.|  
|`StateFile`|Optionaler assetId:///String?qualifyHint=False&autoUpgrade=True\-Parameter.<br /><br /> Gibt die Cachedatei für Timestamps von COM\-Komponenten an.  Falls nicht vorhanden, werden bei jedem Lauf alle Wrapper neu generiert.|  
|`TargetFrameworkVersion`|Optionaler assetId:///String?qualifyHint=False&autoUpgrade=True\-Parameter.<br /><br /> Gibt die Zielframeworkversion für das Projekt an.<br /><br /> Der Standardwert ist `String.Empty`.  d. h., die Verweise werden nicht anhand des Zielframeworks gefiltert.|  
|`TargetProcessorArchitecture`|Optionaler assetId:///String?qualifyHint=False&autoUpgrade=True\-Parameter.<br /><br /> Gibt die bevorzugte Architektur des Zielprozessors an.  Wird nach der Übersetzung an das \/machine\-Flag von tlbimp.exe übergeben.<br /><br /> Der Wert des Parameters sollte ein Member von <xref:Microsoft.Build.Utilities.ProcessorArchitecture> sein.|  
|`TypeLibFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt den Dateipfad der Typbibliothek für COM\-Verweise an.  Die Elemente in diesem Parameter enthalten möglicherweise Elementmetadaten.  Weitere Informationen finden Sie im Abschnitt "TypeLibFiles\-Elementmetadaten" weiter unten.|  
|`TypeLibNames`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die aufzulösenden Typbibliotheknamen an.  Die Elemente in diesem Parameter müssen einige Elementmetadaten enthalten.  Weitere Informationen finden Sie im Abschnitt "TypeLibNames\-Elementmetadaten" weiter unten.|  
|`WrapperOutputDirectory`|Optionaler `String`\-Parameter.<br /><br /> Die Position auf dem Datenträger, an der die generierte Interop\-Assembly gespeichert ist.  Wenn diese Elementmetadaten nicht angegeben sind, verwendet die Aufgabe den absoluten Pfad des Verzeichnisses, in dem sich die Projektdatei befindet.|  
  
## Hinweise  
  
## TypeLibNames\-Elementmetadaten  
 In der folgenden Tabelle werden die verfügbaren Elementmetadaten für die an den `TypeLibNames`\-Parameter übergebenen Elemente beschrieben.  
  
|Metadaten|Description|  
|---------------|-----------------|  
|`GUID`|Erforderliche Elementmetadaten.<br /><br /> Die GUID für die Typbibliothek.  Wenn diese Elementmetadaten nicht angegeben werden, kann die Aufgabe nicht ausgeführt werden.|  
|`VersionMajor`|Erforderliche Elementmetadaten.<br /><br /> Die Hauptversion der Typbibliothek.  Wenn diese Elementmetadaten nicht angegeben werden, kann die Aufgabe nicht ausgeführt werden.|  
|`VersionMinor`|Erforderliche Elementmetadaten.<br /><br /> Die Nebenversion der Typbibliothek.  Wenn diese Elementmetadaten nicht angegeben werden, kann die Aufgabe nicht ausgeführt werden.|  
|`LocaleIdentifier`|Optionale Elementmetadaten.<br /><br /> Der Gebietsschemabezeichner \(oder LCID\) für die Typbibliothek.  Dieser wird als 32\-Bit\-Wert festgelegt, mit dem die von einem Benutzer, in einer Region oder einer Anwendung bevorzugte Sprache angegeben wird.  Wenn diese Elementmetadaten nicht angegeben werden, verwendet die Aufgabe den Standard\-Gebietsschemabezeichner "0".|  
|`WrapperTool`|Optionale Elementmetadaten.<br /><br /> Gibt das Wrappertool an, das zum Generieren des Assemblywrappers für diese Typbibliothek verwendet wird.  Wenn diese Elementmetadaten nicht angegeben werden, verwendet die Aufgabe das Standardwrappertool "tlbimp".  Folgende Optionen von typelibs können ausgewählt werden. Dabei muss die Groß\- und Kleinschreibung beachtet werden.<br /><br /> -   `Primary`: Über dieses Wrappertool können Sie eine bereits generierte primäre Interop\-Assembly für die COM\-Komponente verwenden.  Geben Sie bei Verwendung des Wrappertools kein Wrapperausgabeverzeichnis an, da dadurch Fehler beim Ausführen der Aufgabe auftreten.<br />-   `TLBImp`: Über dieses Wrappertool können Sie eine Interop\-Assembly für die COM\-Komponente generieren.<br />-   `AXImp`: Verwenden Sie dieses Wrappertool, wenn Sie eine Interop\-Assembly für ein ActiveX\-Steuerelement generieren möchten.|  
  
## TypeLibFiles\-Elementmetadaten  
 In der folgenden Tabelle werden die verfügbaren Elementmetadaten für die an den `TypeLibFiles`\-Parameter übergebenen Elemente beschrieben.  
  
|Metadaten|Description|  
|---------------|-----------------|  
|`WrapperTool`|Optionale Elementmetadaten.<br /><br /> Gibt das Wrappertool an, das zum Generieren des Assemblywrappers für diese Typbibliothek verwendet wird.  Wenn diese Elementmetadaten nicht angegeben werden, verwendet die Aufgabe das Standardwrappertool "tlbimp".  Folgende Optionen von typelibs können ausgewählt werden. Dabei muss die Groß\- und Kleinschreibung beachtet werden.<br /><br /> -   `Primary`: Über dieses Wrappertool können Sie eine bereits generierte primäre Interop\-Assembly für die COM\-Komponente verwenden.  Geben Sie bei Verwendung des Wrappertools kein Wrapperausgabeverzeichnis an, da dadurch Fehler beim Ausführen der Aufgabe auftreten.<br />-   `TLBImp`: Über dieses Wrappertool können Sie eine Interop\-Assembly für die COM\-Komponente generieren.<br />-   `AXImp`: Verwenden Sie dieses Wrappertool, wenn Sie eine Interop\-Assembly für ein ActiveX\-Steuerelement generieren möchten.|  
  
> [!NOTE]
>  Je mehr Informationen Sie zur eindeutigen Erkennung einer Typbibliothek eingeben, desto größer ist die Wahrscheinlichkeit, dass die Aufgabe die korrekte Datei auf dem Datenträger auflöst.  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Utilities.Task>\-Klasse.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [Task Base Class](../msbuild/task-base-class.md).  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
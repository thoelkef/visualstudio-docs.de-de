---
title: "MSBuild Targets | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, targets"
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Targets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ziele fassen Aufgaben in einer bestimmten Reihenfolge zusammen und ermöglichen das Unterteilen des Buildprozesses in kleinere Einheiten.  Zur Vorbereitung des Builds kann ein Ziel beispielsweise alle Dateien im Ausgabeverzeichnis löschen, während ein anderes Ziel die Eingaben für das Projekt kompiliert und sie im leeren Verzeichnis ablegt.  Weitere Informationen zu Aufgaben finden Sie unter [Tasks](../msbuild/msbuild-tasks.md).  
  
## Deklarieren von Zielen in der Projektdatei  
 Ziele werden in einer Projektdatei mit dem [Target](../msbuild/target-element-msbuild.md)\-Element deklariert.  Durch den folgenden XML\-Code wird beispielsweise ein Ziel mit dem Namen Construct erstellt, durch das anschießend die Csc\-Aufgabe mit der Compile\-Elementtyp aufgerufen wird.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Wie MSBuild\-Eigenschaften können Ziele neu definiert werden.  Beispiel:  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Wenn AfterBuild ausgeführt wird, zeigt es nur "Second occurence" an.  
  
## Buildreihenfolge für Ziele  
 Wenn die Eingabe für ein Ziel von der Ausgabe eines anderen Ziels abhängt, müssen die Ziele geordnet werden.  Die Reihenfolge, in der die Ziele ausgeführt werden, kann auf unterschiedliche Weise angegeben werden.  
  
-   Ursprüngliche Ziele  
  
-   Standardziele  
  
-   Erstes Ziel  
  
-   Abhängigkeiten der Ziele  
  
-   `BeforeTargets` und `AfterTargets` \(MSBuild 4.0\)  
  
 In keinem Fall wird ein Ziel während eines Builds zweimal ausgeführt, auch dann nicht, wenn ein nachfolgendes Ziel im Build von diesem abhängt.  Sobald ein Ziel ausgeführt wird, ist sein Beitrag zum Build abgeschlossen.  
  
 Ausführliche Informationen zur Buildreihenfolge für Ziele finden Sie unter [Buildreihenfolge für Ziele](../msbuild/target-build-order.md).  
  
## Batchverarbeitung von Zielen  
 Ein Zielelement verfügt möglicherweise über ein `Outputs`\-Attribut, das Metadaten im Format %\(Metadaten\) angibt.  In diesem Fall führt MSBuild das Ziel einmal für jeden eindeutigen Metadatenwert aus und fasst Elemente mit diesem Metadatenwert in einer Batchverarbeitung zusammen.  Beispiel:  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 Fügt die Verweiselemente nach ihren RequiredTargetFramework\-Metadaten zu einem Stapel zusammen.  Die Ausgabe der Ziele sieht wie folgt aus:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
  
```  
  
 Zielbatchverarbeitung wird selten bei tatsächlichen Builds verwendet.  Aufgabenbatchverarbeitung ist eher die Regel.  Weitere Informationen finden Sie unter [Batching](../msbuild/msbuild-batching.md).  
  
## Inkrementelle Builds  
 Inkrementelle Builds sind Buildvorgänge, die so optimiert werden, dass Ziele mit Ausgabedateien, die hinsichtlich der zugehörigen Eingabedateien aktuell sind, nicht ausgeführt werden.  Zielelemente können sowohl über ein `Inputs`\-Attribut, das die Elemente angibt, die das Ziel als Eingabe erwartet, sowie ein `Outputs`\-Attribut verfügen, das die Elemente angibt, die es als Ausgabe erzeugt.  
  
 Wenn alle Ausgabeelemente aktuell sind, überspringt MSBuild das Ziel, wodurch die Buildgeschwindigkeit bedeutend verbessert wird.  Dies wird als inkrementeller Build des Ziels bezeichnet.  Wenn nur einige Dateien aktuell sind, führt MSBuild das Ziel aus, überspringt jedoch die aktuellen Elemente.  Dies wird als partieller inkrementeller Build des Ziels bezeichnet.  Weitere Informationen finden Sie unter [Incremental Builds](../msbuild/incremental-builds.md).  
  
## Siehe auch  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [How to: Use the Same Target in Multiple Project Files](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
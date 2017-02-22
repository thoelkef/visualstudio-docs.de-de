---
title: "How to: Extend the Visual Studio Build Process | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, overriding predefined targets"
  - "MSBuild, overriding DependsOn properties"
  - "MSBuild, extending Visual Studio builds"
  - "MSBuild, DependsOn properties"
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Extend the Visual Studio Build Process
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Buildvorgang wird durch mehrere in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] erstellte TARGETS\-Dateien definiert, die in die Projektdatei importiert werden.  Eine dieser importierten Dateien, Microsoft.Common.targets, kann erweitert werden, um an verschiedenen Stellen im Buildvorgang benutzerdefinierte Aufgaben auszuführen.  In diesem Thema werden zwei Methoden zum Erweitern des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Buildvorgangs beschrieben:  
  
-   Überschreiben bestimmter in Microsoft.Common.targets vordefinierter Ziele  
  
-   Überschreiben der in Microsoft.Common.targets definierten "DependsOn"\-Eigenschaften  
  
## Überschreiben vordefinierter Ziele  
 Die Datei Microsoft.Common.targets enthält einen Satz vordefinierter leerer Ziele, die vor oder nach einigen der Hauptziele im Buildvorgang aufgerufen werden.  Beispielsweise ruft [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] das `BeforeBuild`\-Ziel vor dem `CoreBuild`\-Hauptziel und das `AfterBuild`\-Ziel nach dem `CoreBuild`\-Ziel auf.  Standardmäßig haben die leeren Ziele in Microsoft.Common.targets keine Funktion. Sie können jedoch ihr Standardverhalten überschreiben, indem Sie die gewünschten Ziele in einer Projektdatei definieren, die Microsoft.Common.targets importiert.  Auf diese Weise können Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgaben verwenden und so den Buildvorgang besser steuern.  
  
#### So überschreiben Sie ein vordefiniertes Ziel  
  
1.  Identifizieren Sie ein vordefiniertes Ziel in Microsoft.Common.targets, das Sie überschreiben möchten.  Eine vollständige Liste der Ziele, die Sie bedenkenlos überschreiben können, finden Sie in der nachstehenden Tabelle.  
  
2.  Definieren Sie das Ziel oder die Ziele am Ende der Projektdatei, unmittelbar vor dem `</Project>`\-Tag.  Beispiele:  
  
    ```  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  Erstellen Sie die Projektdatei.  
  
 Die folgende Tabelle enthält eine Übersicht über die Ziele in Microsoft.Common.targets, die Sie bedenkenlos überschreiben können.  
  
|Target Name|Beschreibung|  
|-----------------|------------------|  
|`BeforeCompile`, `AfterCompile`|In einem dieser Ziele eingefügte Aufgaben werden vor oder nach der Kompilierung ausgeführt.  Die meisten Anpassungen erfolgen in einem dieser beiden Ziele.|  
|`BeforeBuild`, `AfterBuild`|In einem dieser Ziele eingefügte Aufgaben werden vor oder nach allen anderen Buildvorgängen ausgeführt. **Note:**  Das `BeforeBuild`\-Ziel und das `AfterBuild`\-Ziel sind bereits in Kommentaren am Ende der meisten Projektdateien definiert.  Dadurch können Sie der Projektdatei mühelos Prä\- und Postbuildereignisse hinzufügen.|  
|`BeforeRebuild`, `AfterRebuild`|In einem dieser Ziele eingefügte Aufgaben werden vor oder nach dem Aufruf der Neuerstellungsfunktion ausgeführt.  Die Ausführungsreihenfolge der Ziele in Microsoft.Common.targets sieht folgendermaßen aus: `BeforeRebuild`, `Clean`, `Build` und dann `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|In einem dieser Ziele eingefügte Aufgaben werden vor oder nach dem Aufruf der Bereinigungsfunktion ausgeführt.|  
|`BeforePublish`, `AfterPublish`|In einem dieser Ziele eingefügte Aufgaben werden vor oder nach dem Aufruf der Veröffentlichungsfunktion ausgeführt.|  
|`BeforeResolveReference`, `AfterResolveReferences`|In einem dieser Ziele eingefügte Aufgaben werden vor oder nach dem Auflösen von Assemblyverweisen ausgeführt.|  
|`BeforeResGen`, `AfterResGen`|In einem dieser Ziele eingefügte Aufgaben werden vor oder nach dem Generieren von Ressourcen ausgeführt.|  
  
## Überschreiben von "DependsOn"\-Eigenschaften  
 Das Überschreiben vordefinierter Ziele ist eine einfache Möglichkeit, den Buildvorgang zu erweitern. Da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] die Definition von Zielen jedoch nacheinander auswertet, lässt sich nicht vermeiden, dass ein anderes Projekt, das Ihr Projekt importiert, die bereits überschriebenen Ziele überschreibt.  Nachdem alle anderen Projekte importiert wurden, ist z. B. das letzte in der Projektdatei definierte `AfterBuild`\-Ziel das Ziel, das während des Buildvorgangs verwendet wird.  
  
 Um sich gegen das unbeabsichtigte Überschreiben von Zielen zu schützen, können Sie die "DependsOn"\-Eigenschaften überschreiben, die in `DependsOnTargets`\-Attributen in der Datei Microsoft.Common.targets verwendet werden.  Beispielsweise enthält das `Build`\-Ziel den `DependsOnTargets`\-Attributwert `"$(BuildDependsOn)"`.  Betrachten Sie das folgende Beispiel:  
  
```  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 Dieser XML\-Abschnitt besagt, dass vor Ausführung des `Build`\-Ziels alle in der `BuildDependsOn`\-Eigenschaft definierten Ziele ausgeführt werden müssen.  Die `BuildDependsOn`\-Eigenschaft ist folgendermaßen definiert:  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Sie können diesen Eigenschaftswert überschreiben, indem Sie am Ende der Projektdatei eine andere Eigenschaft namens `BuildDependsOn` deklarieren.  Durch das Einfügen der vorherigen `BuildDependsOn`\-Eigenschaft in die neue Eigenschaft können Sie am Anfang und am Ende der Zielliste neue Ziele hinzufügen.  Beispiele:  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 Projekte, die die Projektdateien importieren, können diese Eigenschaften überschreiben, ohne die von Ihnen vorgenommenen Anpassungen zu überschreiben.  
  
#### So überschreiben Sie eine "DependsOn"\-Eigenschaft  
  
1.  Identifizieren Sie eine vordefinierte "DependsOn"\-Eigenschaft in Microsoft.Common.targets, die Sie überschreiben möchten.  Eine Liste der häufig überschriebenen "DependsOn"\-Eigenschaften finden Sie in der nachstehenden Tabelle.  
  
2.  Definieren Sie am Ende der Projektdatei eine weitere Instanz der Eigenschaft bzw. Eigenschaften.  Fügen Sie die ursprüngliche Eigenschaft, z. B. `$(BuildDependsOn)`, in die neue Eigenschaft ein.  
  
3.  Definieren Sie Ihre benutzerdefinierten Ziele vor oder nach der Eigenschaftendefinition.  
  
4.  Erstellen Sie die Projektdatei.  
  
### Häufig überschriebene "DependsOn"\-Eigenschaften  
  
|Eigenschaftenname|Beschreibung|  
|-----------------------|------------------|  
|`BuildDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie vor oder nach dem gesamten Buildvorgang benutzerdefinierte Ziele einfügen möchten.|  
|`CleanDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie die Ausgabe aus dem benutzerdefinierten Buildvorgang bereinigen möchten.|  
|`CompileDependsOn`|Die zu überschreibende Eigenschaft, wenn Sie vor oder nach dem Kompilierungsschritt benutzerdefinierte Vorgänge einfügen möchten.|  
  
## Siehe auch  
 [Integration von Visual Studio](../msbuild/visual-studio-integration-msbuild.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [.Targets Files](../msbuild/msbuild-dot-targets-files.md)
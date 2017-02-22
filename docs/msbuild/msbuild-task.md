---
title: "MSBuild-Aufgabe | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#MSBuild"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild-Aufgabe [MSBuild]"
  - "MSBuild, MSBuild-Aufgabe"
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild-Aufgabe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekte aus einem anderen [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekt.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `MSBuild`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`BuildInParallel`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` werden die im `Projects`\-Parameter angegebenen Projekte nach Möglichkeit parallel erstellt.  Der Standardwert ist `false`.|  
|`Projects`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Projektdateien an, die erstellt werden sollen.|  
|`Properties`|Optionaler `String`\-Parameter.<br /><br /> Eine durch Semikolons getrennte Liste der Eigenschaftenname\-Wert\-Paare, die als globale Eigenschaften auf das untergeordnete Projekt angewendet sollen.  Die Angabe dieses Parameters entspricht funktional dem Festlegen von Eigenschaften mit dem **\/property**\-Schalter beim Erstellen mit [MSBuild.exe](../msbuild/msbuild-command-line-reference.md).  Beispiel:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Wenn Eigenschaften über den `Properties`\-Parameter an das Projekt übergeben werden, erstellt [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] eine neue Instanz des Projekts, selbst wenn die Projektdatei schon geladen wurde.  Nach der Erstellung einer neuen Instanz des Projekts wird es von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] als anderes Projekt mit anderen globalen Eigenschaften behandelt, das parallel mit anderen Instanzen des Projekts erstellt werden kann.  Beispielsweise könnte eine Releasekonfiguration gleichzeitig mit einer Debugkonfiguration erstellt werden.|  
|`RebaseOutputs`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, werden die relativen Pfade von Zielausgabeelementen aus den erstellten Projekten so angepasst, dass sie sich auf das aufrufende Projekt beziehen.  Der Standardwert ist `false`.|  
|`RemoveProperties`|Optionaler `String`\-Parameter.<br /><br /> Gibt den Satz zu entfernender globaler Eigenschaften an.|  
|`RunEachTargetSeparately`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` werden die Ziele in der Liste von der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgabe einzeln und nicht gleichzeitig an [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] übergeben.  Durch das Festlegen dieses Parameters auf `true` wird garantiert, dass nachfolgende Ziele aufgerufen werden, auch wenn bei vorher aufgerufenen Zielen ein Fehler aufgetreten ist.  Andernfalls würde ein Buildfehler den Aufruf aller nachfolgenden Ziele beenden.  Der Standardwert ist `false`.|  
|`SkipNonexistentProjects`|Optionaler `Boolean`\-Parameter.<br /><br /> Beim Wert `true` werden auf dem Datenträger nicht vorhandene Projektdateien übersprungen.  Andernfalls werden solche Projekte einen Fehler verursachen.|  
|`StopOnFirstFailure`|Optionaler `Boolean`\-Parameter.<br /><br /> Falls `true`, wenn eines der Projekte nicht erstellt werden kann, werden keine weiteren Projekte erstellt.  Derzeit wird dies bei paralleler Erstellung \(mit mehreren Prozessoren\) nicht unterstützt.|  
|`TargetAndPropertyListSeparators`|Optionaler `String[]`\-Parameter.<br /><br /> Gibt eine Liste der Ziele und Eigenschaften als `Project`\-Elementmetadaten an.\)  Bei Separatoren werden Escapezeichen vor der Verarbeitung entfernt.  z .. . %3B \(ein mit Escapezeichen "; "\) wird behandelt, als ob es UN\-entwichen "wurde; ".|  
|`TargetOutputs`|Optionaler schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Gibt die Ausgaben der erstellten Ziele von allen Projektdateien zurück.  Es werden nur die Ausgaben der angegebenen Ziele zurückgegeben, jedoch keine Ausgaben, die möglicherweise für Ziele vorhanden sind, von denen diese Ziele abhängen.<br /><br /> Der `TargetOutputs`\-Parameter enthält außerdem die folgenden Metadaten:<br /><br /> -   `MSBuildSourceProjectFile`: Die [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei, die das Ziel enthält, das die Ausgaben festgelegt hat.<br />-   `MSBuildSourceTargetName`: Das Ziel, das die Ausgaben festgelegt hat. **Note:**  Wenn Sie die Ausgaben für jede Projektdatei oder jedes Ziel separat ermitteln möchten, führen Sie die `MSBuild`\-Aufgabe für jede Projektdatei bzw. jedes Ziel separat aus.  Wenn Sie die `MSBuild`\-Aufgabe nur einmal ausführen, um alle Projektdateien zu erstellen, werden die Ausgaben aller Ziele in einem Array zusammengefasst.|  
|`Targets`|Optionaler `String`\-Parameter.<br /><br /> Gibt das Ziel oder die Ziele für die Erstellung der Projektdateien an.  Trennen Sie mehrere Zielnamen in der Liste durch Semikolons voneinander.  Wenn in der `MSBuild`\-Aufgabe keine Ziele angegeben sind, werden die in den Projektdateien angegebenen Standardziele erstellt. **Note:**  Die Ziele müssen in allen Projektdateien vorhanden sein.  Andernfalls tritt ein Buildfehler auf.|  
|`ToolsVersion`|Optionaler `String`\-Parameter.<br /><br /> Gibt die `ToolsVersion` an, die beim Erstellen von Projekten an diese Aufgabe übergeben wird.<br /><br /> Ermöglicht einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgabe das Erstellen eines Projekts für eine andere als die im Projekt angegebene Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Gültige Werte sind `2.0`, `3.0` und `3.5`.  Der Standardwert lautet `3.5`.|  
|`UnloadProjectsOnCompletion`|Optionaler `Boolean`\-Parameter.<br /><br /> Beim Wert `true` wird das Projekt nach Abschluss des Vorgangs entladen.|  
|`UseResultsCache`|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird das zwischengespeicherte Ergebnis, wenn vorhanden, zurückgegeben.  Wenn die MSBuild\-Aufgabe ausgeführt wird, wird das Ergebnis in einem Bereich \(ProjectFileName, GlobalProperties\)\[TargetNames\] zwischengespeichert werden<br /><br /> als Liste von Build\-Elementen|  
  
## Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
 Anders als beim Aufrufen von MSBuild.exe über die [Exec Task](../msbuild/exec-task.md) wird bei dieser Aufgabe derselbe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Prozess verwendet, um die untergeordneten Projekte zu erstellen.  Die Liste mit bereits erstellten Zielen, die übersprungen werden können, wird von übergeordneten und untergeordneten Builds gemeinsam genutzt.  Diese Aufgabe nimmt außerdem weniger Zeit in Anspruch, da kein neuer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Prozess erstellt wird.  
  
 Diese Aufgabe kann nicht nur Projektdateien verarbeiten, sondern auch Projektmappendateien.  
  
 Alle Konfigurationen, die von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zum gleichzeitigen Erstellen von Projekten benötigt werden, müssen mithilfe einer Konfigurationsdatei konfigurierbar gemacht werden, auch wenn eine Konfiguration Remoteinfrastruktur \(z. B. Ports, Protokolle, Timeouts, Wiederholungen usw.\) umfasst.  Nach Möglichkeit sollten Konfigurationselemente in der `MSBuild`\-Aufgabe als Aufgabenparameter angegeben werden.  
  
 Ab [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 bringen Projektmappenprojekte TargetOutputs aus allen hiermit erstellten Unterprojekten hervor.  
  
## Übergeben von Eigenschaften an Projekte  
 In den [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Versionen vor [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 war das Übergeben unterschiedlicher Eigenschaftensätze an verschiedene im [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Element aufgeführte Projekte sehr schwierig.  Bei der Verwendung des Eigenschaftenattributs der [MSBuild Task](../msbuild/msbuild-task.md) wurde ihre Einstellung auf alle zu erstellenden Projekte angewendet. Um das zu verhindern, musste die [MSBuild Task](../msbuild/msbuild-task.md) unter Angabe unterschiedlicher Eigenschaften für jedes Projekt in der Elementliste als Batch verarbeitet werden.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 bietet jedoch zwei neue reservierte Metadatenelemente, Properties und AdditionalProperties. Sie gewährleisten die Flexibilität, die zur Übergabe unterschiedlicher Eigenschaften für verschiedene mit der [MSBuild Task](../msbuild/msbuild-task.md) erstellte Projekte erforderlich ist.  
  
> [!NOTE]
>  Diese neuen Metadatenelemente sind nur auf Elemente anwendbar, die im Projektattribut der [MSBuild Task](../msbuild/msbuild-task.md) übergeben werden.  
  
## Multiprozessor\-Buildvorteile  
 Einer der größten Vorteile dieser neuen Metadaten wird offensichtlich, wenn Sie Projekte parallel auf einem Mehrprozessorsystem erstellen.  Die Metadaten ermöglichen die Konsolidierung aller Projekte in einem [MSBuild Task](../msbuild/msbuild-task.md)\-Aufruf, ohne dass Batchverarbeitung oder bedingte [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] \-Aufgaben ausgeführt werden müssen.  Sie brauchen nur eine einzige [MSBuild Task](../msbuild/msbuild-task.md) aufzurufen, und alle im Projektattribut aufgeführten Projekte werden parallel erstellt.  \(Dazu muss jedoch das `BuildInParallel=true`\-Attribut in der [MSBuild Task](../msbuild/msbuild-task.md) vorhanden sein.\) Weitere Informationen finden Sie unter [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## Properties\-Metadaten  
 Ein häufiges Szenario ist die Erstellung mehrerer Projektmappendateien mit der [MSBuild Task](../msbuild/msbuild-task.md) unter Verwendung unterschiedlichen Buildkonfigurationen.  Sie können Projektmappe a1 mit der Debugkonfiguration und Projektmappe a2 mit der Releasekonfiguration erstellen.  In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 würde diese Projektdatei wie folgt aussehen:  
  
> [!NOTE]
>  Im folgenden Beispiel stellt "…" zusätzliche Projektmappendateien dar.  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Durch die Verwendung der Properties\-Metadaten können Sie diesen Vorgang vereinfachen und eine einzige [MSBuild Task](../msbuild/msbuild-task.md) verwenden, wie nachfolgend dargestellt:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- oder \-  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## AdditionalProperties\-Metadaten  
 Erwägen Sie beim Erstellen von zwei Projektmappendateien mit der [MSBuild Task](../msbuild/msbuild-task.md) folgendes Szenario: Für beide Projektmappendateien wird die Releasekonfiguration verwendet, aber eine verwendet die x86\-Architektur und die andere die ia64\-Architektur.  In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 müssten Sie mehrere Instanzen der [MSBuild Task](../msbuild/msbuild-task.md) erstellen, nämlich eine zum Erstellen des Projekts mit der Releasekonfiguration und der x86\-Architektur, und eine zweite, die die Releasekonfiguration mit der ia64\-Architektur verwendet.  Die Projektdatei würde wie folgt aussehen:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 Durch die Verwendung der AdditionalProperties\-Metadaten können Sie diesen Vorgang vereinfachen und eine einzige [MSBuild Task](../msbuild/msbuild-task.md) verwenden, wie nachfolgend dargestellt:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## Beispiel  
 Im folgenden Beispiel wird die `MSBuild`\-Aufgabe verwendet, um die von der `ProjectReferences`\-Elementauflistung angegebenen Projekte zu erstellen.  Die sich ergebenden Zielausgaben werden in der `AssembliesBuiltByChildProjects`\-Elementauflistung gespeichert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
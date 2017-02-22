---
title: "Target-Element (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Target"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Target-Element [MSBuild]"
  - "<Target>-Element [MSBuild]"
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Target-Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält Aufgaben, die [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sequenziell ausführen soll.  
  
## Syntax  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Ziels.|  
|`Condition`|Optionales Attribut.<br /><br /> Die Bedingung wird ausgewertet.  Wenn die Bedingung `false` ergibt, werden die Aufgaben des Ziels oder der ggf. im `DependsOnTargets`\-Attribut festgelegten Ziele nicht ausgeführt.  Weitere Informationen zu Bedingungen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Optionales Attribut.<br /><br /> Die Dateien, die Eingaben in dieses Ziel besteht.  Mehrere Dateien werden durch Semikolons getrennt.  Die Timestamps der Dateien werden mit den Timestamps von Dateien in `Outputs` verglichen, um zu ermitteln, ob `Target` auf dem neuesten Stand ist.  Weitere Informationen finden Sie unter [Incremental Builds](../msbuild/incremental-builds.md), [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md) und [Transforms](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Optionales Attribut.<br /><br /> Die Dateien, die Ausgaben in dieses Ziel besteht.  Mehrere Dateien werden durch Semikolons getrennt.  Die Timestamps der Dateien werden mit den Timestamps von Dateien in `Inputs` verglichen, um zu ermitteln, ob `Target` auf dem neuesten Stand ist.  Weitere Informationen finden Sie unter [Incremental Builds](../msbuild/incremental-builds.md), [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md) und [Transforms](../msbuild/msbuild-transforms.md).|  
|`Returns`|Optionales Attribut.<br /><br /> Der Satz der Elemente, die für Aufgaben verfügbar gemacht werden, die dieses Ziel, z. B. MSBuild\-Aufgaben, aufrufen.  Mehrere Ziele werden durch Semikolons getrennt.  Wenn die Ziele in der Datei keine `Returns`\-Attribute haben, werden die Ausgabeattribute stattdessen zu diesem Zweck verwendet wird.|  
|`KeepDuplicateOutputs`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, mehrere Verweise auf dasselbe Element in der EINGABETASTE des Ziels aufgezeichnet werden.  Standardmäßig ist dieses Attribut `false`.|  
|`BeforeTargets`|Optionales Attribut.<br /><br /> Eine durch Semikolon getrennte Liste von Zielnamen. Wenn Sie angegeben werden, gibt an, dass dieses Ziel ausgeführt werden sollte vor das angegebene Ziel oder die Ziele.  So kann der Projektautor einen vorhandenen Satz von Ziele erweitern, ohne sie direkt zu ändern.  Weitere Informationen finden Sie unter [Buildreihenfolge für Ziele](../msbuild/target-build-order.md).|  
|`AfterTargets`|Optionales Attribut.<br /><br /> Eine durch Semikolon getrennte Liste von Zielnamen.  Wenn Sie angegeben werden, gibt an, dass dieses Ziel ausgeführt werden sollte nach das angegebene Ziel oder die Ziele.  So kann der Projektautor einen vorhandenen Satz von Ziele erweitern, ohne sie direkt zu ändern.  Weitere Informationen finden Sie unter [Buildreihenfolge für Ziele](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Optionales Attribut.<br /><br /> Die Ziele, die ausgeführt werden müssen, bevor dieses Ziel ausgeführt werden kann oder eine Analyse der Abhängigkeit auf der höchsten Ebene erfolgen kann.  Mehrere Ziele werden durch Semikolons getrennt.|  
|`Label`|Optionales Attribut.<br /><br /> Ein Bezeichner, der System\- und Benutzerelemente identifizieren oder sortieren kann.|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Aufgabe](../msbuild/task-element-msbuild.md)|Erstellt eine Instanz einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgabe und führt diese aus.  Es kann keine oder mehrere Aufgaben in einem Ziel geben.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Enthält einem Satz benutzerdefinierte `Property`\-Elemente.  Ab .NET Framework 3.5, enthält möglicherweise ein `Target`\-Element `PropertyGroup`\-Elemente.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Enthält einem Satz benutzerdefinierte `Item`\-Elemente.  Ab .NET Framework 3.5, enthält möglicherweise ein `Target`\-Element `ItemGroup`\-Elemente.  Weitere Informationen finden Sie unter [Items](../msbuild/msbuild-items.md).|  
|[OnError](../msbuild/onerror-element-msbuild.md)|Ruft eine oder mehrere Ziele auszuführen, wenn das Attribut `ContinueOnError` ErrorAndStop \(oder `false`\) für eine fehlgeschlagene Aufgabe ist.  Es kann keine oder mehrere `OnError`\-Elemente in einem Ziel geben.  Wenn `OnError`\-Elemente vorhanden sind, müssen diese die letzten Elemente im `Target`\-Element sein.<br /><br /> Informationen zum `ContinueOnError`\-Attribut, finden Sie unter [Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md).|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei.|  
  
## Hinweise  
 Das erste auszuführende Ziel wird zur Laufzeit angegeben.  Ziele können von anderen Zielen abhängig sein.  So ist z. B. ein Bereitstellungsziel von einem Kompilierungsziel abhängig.  Das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Modul führt Abhängigkeiten in der Reihenfolge aus, in der sie im `DependsOnTargets`\-Attribut angezeigt werden \(von links nach rechts\).  Weitere Informationen finden Sie unter [Targets](../msbuild/msbuild-targets.md).  
  
 Ein Ziel wird während eines Buildvorgangs nur einmal ausgeführt, auch wenn mehrere Ziele von diesem abhängig sind.  
  
 Wenn ein Ziel übersprungen wird, da das entsprechende `Condition`\-Attribut `false` ergibt, kann es trotzdem ausgeführt werden, wenn es zu einem späteren Zeitpunkt im Buildvorgang aufgerufen wird und das `Condition`\-Attribut dann `true` ergibt.  
  
 Vor MSBuild 4 gab `Target` alle Elemente zurück, die im `Outputs`\-Attribut angegeben wurden.  MSBuild muss zu diesem Zweck diese Elemente aufzeichnen, falls spätere Aufgaben im Build sie anfordern.  Da es keine Möglichkeit gab, anzugeben, welche Ziele Ausgänge hatten, die Aufrufer anfordern würden, sammelte MSBuild alle Elemente aus allen `Outputs` für alle aufgerufenen `Target`s.  Dieses führt zu Skalierungsprobleme bei Builds, die eine große Anzahl von Ausgabeelementen haben.  
  
 Wenn der Benutzer ein `Returns` für ein beliebiges `Target`\-Element in einem Projekt angibt, dann zeichnen nur die `Target`s mit dem `Returns` Attribut diese Elemente auf.  
  
 Ein `Target` kann `Outputs` Attribut und ein `Returns` \-Attribut enthalten.  `Outputs` wird mit `Inputs` verwendet, um festzustellen, ob das Ziel auf dem neuesten Stand ist.  `Returns`, sofern vorhanden, überschreibt den Wert von `Outputs`, um zu bestimmen, welche Elemente an Aufrufer zurückgegeben werden.  Wenn `Returns` nicht vorhanden ist, dann wird `Outputs` für Anrufer, außer im oben beschriebenen Fall, bereitgestellt werden.  
  
 Vor MSBuild 4 wurde jedes Mal, wenn ein `Target` mehrere Verweise auf dasselbe Element in den `Outputs` enthielt, diese doppelten Elemente aufgezeichnet.  In sehr großen Builds, die eine große Anzahl von Ausgaben und viele Projektabhängigkeiten hatten, würde dies dazu führen, dass eine große Menge an Arbeitsspeicher verschwendet wird, weil die doppelten Elemente nicht von Nutzen waren.  Wenn das \- Attribut auf `KeepDuplicateOutputs``true` festgelegt ist, werden diese Duplikate aufgezeichnet.  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `Target`\-Element veranschaulicht, das die `Csc`\-Aufgabe ausführt.  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## Siehe auch  
 [Targets](../msbuild/msbuild-targets.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)
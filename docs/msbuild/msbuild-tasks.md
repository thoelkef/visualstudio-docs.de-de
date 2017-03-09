---
title: "MSBuild-Aufgaben | Microsoft Docs"
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
  - "Aufgaben"
  - "MSBuild-Aufgaben"
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild-Aufgaben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Buildplattform benötigt die Fähigkeit, eine beliebige Anzahl von Aktionen während des Buildprozesses auszuführen. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verwendet *Aufgaben* zum Ausführen dieser Aktionen. Eine Aufgabe ist eine Einheit von ausführbarem Code verwendet werden, indem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] atomare Vorgänge ausführen.  
  
## <a name="task-logic"></a>Task-Logik  
 Die [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML-Projektdateiformat kann nicht vollständig ausgeführt werden Vorgänge für eine eigene, sodass die Aufgabenlogik müssen, außerhalb der Projektdatei implementiert werden erstellen.  
  
 Die Ausführungslogik einer Aufgabe wird als eine Klasse von .NET, implementiert implementiert die <xref:Microsoft.Build.Framework.ITask> -Schnittstelle, definiert in der <xref:Microsoft.Build.Framework> Namespace.  
  
 Die Task-Klasse definiert auch die verfügbaren Eingabe- und Parameter an die Aufgabe in der Projektdatei. Alle konfigurierbare öffentliche nicht statischen und nicht abstrakten Eigenschaften, die von der Aufgabenklasse verfügbar gemacht werden können in der Projektdatei zugegriffen werden, durch die Platzierung eines entsprechenden Attributs mit demselben Namen auf die [Task](../msbuild/task-element-msbuild.md) Element.  
  
 Sie können eine eigene Aufgabe schreiben, erstellen Sie eine verwaltete Klasse, die implementiert die <xref:Microsoft.Build.Framework.ITask> Schnittstelle. Weitere Informationen finden Sie unter [Schreiben von Aufgaben](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Ausführen einer Aufgabe aus einer Projektdatei  
 Vor dem Ausführen einer Aufgabe in der Projektdatei, müssen Sie zuerst den Typ in der Assembly, die die Aufgabe für den Aufgabennamen mit implementiert Zuordnen der [UsingTask](../msbuild/usingtask-element-msbuild.md) Element. Auf diese Weise können [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] erkennen, wo sich die Ausführungslogik der Aufgabe beim Auffinden in der Projektdatei.  
  
 Zum Ausführen einer Aufgabe in einem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Projektdatei, erstellen Sie ein Element mit dem Namen der Aufgabe als untergeordnetes Element des ein `Target` Element. Wenn eine Aufgabe Parameter akzeptiert, werden diese als Attribute des Elements übergeben.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Artikel können Listen und Eigenschaften als Parameter verwendet werden. Z. B. im folgenden code wird die `MakeDir` Aufgabe und legt den Wert der die `Directories` Eigenschaft der `MakeDir` Objekt gleich dem Wert von der `BuildDir` Eigenschaft deklariert wird, im vorherigen Beispiel.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Aufgaben können Informationen auch aus der Projektdatei zurückgeben, die Elemente oder Eigenschaften für die spätere Verwendung gespeichert werden können. Z. B. im folgenden code wird die `Copy` Aufgabe und speichert die Informationen aus der `CopiedFiles` Ausgabeeigenschaft in der `SuccessfullyCopiedFiles` Liste.  
  
```  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Bereits enthaltene Aufgaben  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wird mit zahlreichen Aufgaben, wie z. B. [Kopie](../msbuild/copy-task.md), Kopieren von Dateien, [MakeDir](../msbuild/makedir-task.md), Erstellen von Verzeichnissen und [Csc](../msbuild/csc-task.md), welche kompiliert [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Quellcodedateien. Eine vollständige Liste der verfügbaren Aufgaben sowie Nutzungsinformationen finden Sie unter [Aufgabenreferenz](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Überschriebene Aufgaben  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Sucht nach Aufgaben an verschiedenen Orten. Der erste Speicherort ist in Dateien mit der Erweiterung. Außerkraftsetzen in den .NET Framework-Verzeichnissen gespeichert. Aufgaben in diesen Dateien überschreiben alle anderen Aufgaben mit den gleichen Namen, einschließlich Aufgaben in der Projektdatei. Der zweite Speicherort ist in Dateien mit der Erweiterung. Aufgaben in den .NET Framework-Verzeichnissen. Wenn der Task nicht in einem dieser beiden Speicherorte gefunden wird, wird die Aufgabe in der Projektdatei verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild-Konzepte](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild1.md)   
 [Schreiben von Aufgaben](../msbuild/task-writing.md)   
 [Inline-Tasks](../msbuild/msbuild-inline-tasks.md)
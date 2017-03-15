---
title: "Buildreihenfolge f&#252;r Ziele | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, Buildreihenfolge"
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Buildreihenfolge f&#252;r Ziele
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn die Eingabe für ein Ziel von der Ausgabe eines anderen Ziels abhängt, müssen die Ziele geordnet werden.  Sie können diese Attribute verwenden, um die Reihenfolge, in der die Ziele ausgeführt werden:  
  
-   `InitialTargets`.  Dies `Project`\-Attribut gibt die Ziele an, die zuerst ausgeführt werden, selbst wenn Ziele in der Befehlszeile oder `DefaultTargets` im \- Attribut angegeben werden.  
  
-   `DefaultTargets`.  Dies `Project` atttribute gibt an, welche Ziele ausgeführt werden, wenn in der Befehlszeile kein Ziel explizit angegeben wird.  
  
-   `DependsOnTargets`.  Dieses Attribut gibt `Target` Ziele an, die ausgeführt werden müssen, bevor dieses Ziel ausgeführt werden kann.  
  
-   `BeforeTargets` und `AfterTargets`.  Diese `Target`\-Attribute geben an, dass dieses Ziel vor oder nach den angegebenen Zielen \(MSBuild 4.0\) ausgeführt werden soll.  
  
 In keinem Fall wird ein Ziel während eines Builds zweimal ausgeführt, auch dann nicht, wenn ein nachfolgendes Ziel im Build von diesem abhängt.  Sobald ein Ziel ausgeführt wurde, ist sein Beitrag zum Build abgeschlossen.  
  
 Ziele können ein `Condition`\-Attribut besitzen.  Wenn die angegebene Bedingung zu `false` ergibt, wird das Ziel nicht ausgeführt und hat keine Auswirkungen auf den Build.  Weitere Informationen zu Bedingungen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).  
  
## Ursprüngliche Ziele  
 Das \- Attribut des \- Elements `InitialTargets`[Projekt](../msbuild/project-element-msbuild.md) gibt Ziele auf, die zuerst ausgeführt werden, selbst wenn Ziele in der Befehlszeile oder `DefaultTargets` im \- Attribut angegeben werden.  Die ursprünglichen Ziele werden in der Regel zur Fehlerprüfung verwendet.  
  
 Der Wert des \- Attributs kann `InitialTargets`, sortierte Liste eine durch Semikolons getrenntes sein von Zielen.  Im folgenden Beispiel wird die `Warm` Tool und dann die `Eject` Tool an.  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Importierte Projekte können eigene `InitialTargets`\-Attribute besitzen.  Alle ursprünglichen Ziele werden zusammen aggregiert und in der festgelegten Reihenfolge ausgeführt.  
  
 Weitere Informationen finden Sie unter [How to: Specify Which Target to Build First](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## Standardziele  
 Das \- Attribut des \- Elements `DefaultTargets`[Projekt](../msbuild/project-element-msbuild.md) gibt an, das Ziele erstellt werden, wenn ein Ziel explizit nicht in einer Befehlszeile angegeben wird.  
  
 Der Wert des \- Attributs kann `DefaultTargets`, sortierte Liste eine durch Semikolons getrenntes sein von Standardzielen.  Im folgenden Beispiel wird die `Clean` Tool und dann die `Build` Tool an.  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Sie können die Standardziele überschreiben, indem Sie den **\/target** Schalter in der Befehlszeile verwenden.  Im folgenden Beispiel wird die `Build` Tool und dann die `Report` Tool an.  Wenn Sie Ziele auf diese Weise angeben, werden alle Standardziele ignoriert.  
  
 `msbuild /target:Build;Report`  
  
 Wenn ursprüngliche Ziele und Standardziele angegeben werden und wenn keine Befehlszeilenziele angegeben werden, führt MSBuild zuerst die ursprünglichen Ziele und dann die Standardziele ausgeführt.  
  
 Importierte Projekte können eigene `DefaultTargets`\-Attribute besitzen.  Das erste gefundene `DefaultTargets`\-Attribut bestimmt die Standardziele, die ausgeführt werden.  
  
 Weitere Informationen finden Sie unter [How to: Specify Which Target to Build First](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## Erstes Ziel  
 Wenn keine ursprünglichen Ziele, Standardziele oder Befehlszeilenziele angegeben wurden, wird von MSBuild das erste in der Projektdatei oder einer beliebigen importierten Projektdatei gefundene Ziel ausgeführt.  
  
## Abhängigkeiten der Ziele  
 Ziele können untereinander Abhängigkeitsbeziehungen besitzen.  Das `DependsOnTargets`\-Attribut gibt an, dass ein Ziel von anderen Zielen abhängig ist.  Beispiel:  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 weist MSBuild an, dass das `Serve` Ziel vom `Chop` Ziel und vom `Cook` Ziel abhängig ist.  MSBuild führt das `Chop` Ziel aus und führt dann das `Cook` Ziel aus, bevor das `Serve` Ziel ausgeführt wird.  
  
## Vor Zielen und nach Ziele  
 In MSBuild 4.0 können Sie Reihenfolge der Ziele mit dem `BeforeTargets`\-Attribut und dem `AfterTargets`\-Attribut angeben.  
  
 Betrachten Sie das folgende Skript:  
  
```  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 So `Optimize` Optimize\-Zwischenziel erstellen, das nach dem `Compile` Ziel ausgeführt wird, und zwar bevor das `Link` Ziel, das folgende Ziel an einer beliebigen Stelle im `Project`\-Element hinzufügen.  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## Bestimmen der Buildreihenfolge für Ziele  
 MSBuild bestimmt die Buildreihenfolge der Ziele wie folgt:  
  
1.  `InitialTargets` Ziele werden ausgeführt.  
  
2.  Ziele, die in der Befehlszeile durch den **\/target**\-Schalter angegeben wurden, werden ausgeführt.  Wenn Sie keine Ziele in der Befehlszeile angeben, werden die `DefaultTargets` Ziele ausgeführt.  Wenn kein vorhanden ist, wird das erste gefundene Ziel ausgeführt.  
  
3.  Das `Condition`\-Attribut des Ziels wird ausgewertet.  Wenn das `Condition`\-Attribut vorhanden ist und zu `false` ergibt, wird das Ziel nicht ausgeführt und keine weiteren Auswirkungen auf den Build.  
  
4.  Vor dem Ausführen eines Ziels werden dessen `DependsOnTargets`\-Ziele ausgeführt.  
  
5.  Vor dem Ausführen eines Ziels wird jedes Ziel ausgeführt, das dieses in einem `BeforeTargets`\-Attribut aufführt.  
  
6.  Vor dem Ausführen eines Ziels werden dessen `Inputs`\-Attribut und `Outputs`\-Attribut verglichen.  Wenn MSBuild ermittelt, dass alle Ausgabedateien hinsichtlich der zugehörigen Eingabedatei oder \- dateien veraltet sind, führt MSBuild das Ziel aus.  Andernfalls überspringt MSBuild das Ziel.  
  
7.  Nachdem ein Ziel ausgeführt oder übersprungen wurde, wird jedes Ziel ausgeführt, das dieses in einem `AfterTargets`\-Attribut aufführt.  
  
## Siehe auch  
 [Targets](../msbuild/msbuild-targets.md)
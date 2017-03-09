---
title: "Gewusst wie: Angeben des zuerst zu erstellenden Ziels | Microsoft Docs"
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
  - "DefaultTargets-Attribut [MSBuild]"
  - "MSBuild und Festlegen des Standardziels"
  - "MSBuild DefaultTargets-Attribut"
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Angeben des zuerst zu erstellenden Ziels
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Projektdatei kann eine oder mehrere enthalten `Target` Elemente, die definieren, wie das Projekt erstellt wird. Die [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) Modul erstellt, das erste Projekt er sucht und Abhängigkeiten, es sei denn, die Projektdatei enthält ein `DefaultTargets` -Attribut, ein `InitialTargets` Attribut oder ein Ziel angegeben ist, an der Befehlszeile mit der **/target** wechseln.  
  
## <a name="using-the-initialtargets-attribute"></a>Verwenden des InitialTargets-Attributs  
 Die `InitialTargets` -Attribut des der `Project` Element gibt ein Ziel, das zuerst ausgeführt wird, auch wenn Ziele, in der Befehlszeile oder in angegeben sind der `DefaultTargets` Attribut.  
  
#### <a name="to-specify-one-initial-target"></a>Ein ursprüngliches Ziel angeben  
  
-   Geben Sie das Standardziel in der `InitialTargets` -Attribut des der `Project` Element. Zum Beispiel:  
  
     `<Project InitialTargets="Clean">`  
  
 Sie können mehrere ursprünglichen Ziele im Angeben der `InitialTargets` Attribut, indem Sie die Ziele nacheinander aufführen und mithilfe eines Semikolons voneinander trennen. Die Ziele in der Liste werden nacheinander ausgeführt.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Mehr als ein ursprüngliches Ziel angeben  
  
-   Listen Sie die ursprünglichen Ziele durch Semikolons getrennt ein, in dem `InitialTargets` -Attribut des der `Project` Element. Zum Ausführen des Beispiels die `Clean` Ziel und dann die `Compile` Geben Sie als Ziel:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Verwenden das DefaultTargets-Attribut  
 Das `DefaultTargets` -Attribut des der `Project` Element gibt das Ziel bzw. die Ziele erstellt werden, wenn ein Ziel nicht explizit in der Befehlszeile angegeben wird. Wenn beide Ziele angegeben sind die `InitialTargets` und `DefaultTargets` Attribute und kein Ziel angegeben ist, in der Befehlszeile [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] im angegebenen Ziele ausgeführt der `InitialTargets` Attribut gefolgt von den Zielen, die im angegebenen die `DefaultTargets` Attribut.  
  
#### <a name="to-specify-one-default-target"></a>Ein Standardziel angeben  
  
-   Geben Sie das Standardziel in der `DefaultTargets` -Attribut des der `Project` Element. Zum Beispiel:  
  
     `<Project DefaultTargets="Compile">`  
  
 Sie können mehr als ein Standardziel im Angeben der `DefaultTargets` Attribut, indem Sie die Ziele nacheinander aufführen und mithilfe eines Semikolons voneinander trennen. Die Ziele in der Liste werden nacheinander ausgeführt.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Mehr als ein Standardziel angeben  
  
-   Listen Sie die Standardziele durch Semikolons getrennt ein, in dem `DefaultTargets` -Attribut des der `Project` Element. Zum Ausführen des Beispiels die `Clean` Ziel und dann die `Compile` Geben Sie als Ziel:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Mithilfe des Schalters/target  
 Wenn ein Standardziel ist nicht in der Projektdatei definiert, oder wenn Sie nicht das Standardziel verwenden möchten, Sie die Befehlszeilenoption können **/target** an ein anderes Ziel angeben. Ziele angegeben, mit der **/target** Switch ausgeführt wird, anstelle der festgelegten Ziele der `DefaultTargets` Attribut. Im angegebenen Ziele der `InitialTargets` Attribut immer zuerst ausgeführt.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Ein anderes Ziel als Standardziel zuerst verwendet.  
  
-   Geben Sie das Ziel als das erste Ziel mithilfe der **/target** Befehlszeilenschalter. Zum Beispiel:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Mehrere Ziele als die Standardziele zuerst verwendet.  
  
-   Listen Sie die Ziele, getrennt durch Semikolons oder Kommas, mit der **/target** Befehlszeilenschalter. Zum Beispiel:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Siehe auch
  [MSBuild](../msbuild/msbuild1.md)  
 [Ziele](../msbuild/msbuild-targets.md)   
 [Gewusst wie: Bereinigen eines Builds](../msbuild/how-to-clean-a-build.md)
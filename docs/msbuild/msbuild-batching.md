---
title: MSBuild-Batchverarbeitung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd009d67fdd4402ed80a6052be8ba877e30e4560
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017226"
---
# <a name="msbuild-batching"></a>MSBuild-Batchverarbeitung
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kann Elementlisten basierend auf den Elementmetadaten in verschiedene Kategorien oder Batches unterteilen und ein Ziel oder eine Aufgabe einmal mit jedem Batch ausführen.  
  
## <a name="task-batching"></a>Aufgabenbatchverarbeitung  
 Durch die Aufgabenbatchverarbeitung können Sie Ihre Projektdateien vereinfachen, indem Sie Elementlisten in verschiedene Batches unterteilen und jeden dieser Batches separat an eine Aufgabe übergeben können. Dies bedeutet, dass die Aufgabe und ihre Attribute für eine Projektdatei nur einmal deklariert werden müssen, obwohl sie mehrmals ausgeführt werden können.  
  
 Sie geben an, dass [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] die Batchverarbeitung mit einer Aufgabe ausführen soll, indem Sie die Notation %(\<ItemMetaDataName>) in einem der Attribute der Aufgabe verwenden. Im folgenden Beispiel wird die `Example`-Elementliste basierend auf dem `Color`-Elementmetadatenwert in Batches aufgeteilt, und alle Batches werden separat an die `MyTask`-Aufgabe übergeben.  
  
> [!NOTE]
>  Wenn Sie an keiner anderen Stelle in den Attributen der Aufgabe auf die Elementliste verweisen oder der Metadatenname mehrdeutig sein kann, können Sie die Notation %(\<ItemCollection.ItemMetaDataName>) verwenden, um die Elementmetadaten vollständig für die Batchverarbeitung zu qualifizieren.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Weitere Beispiele für die Batchverarbeitung finden Sie unter [Elementmetadaten bei der Aufgabenbatchverarbeitung](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Zielbatchverarbeitung  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] überprüft, ob die Eingaben und Ausgaben eines Ziels aktuell sind, bevor das Ziel ausgeführt wird. Wenn die Eingaben und Ausgaben aktuell sind, wird das Ziel übersprungen. Wenn eine Aufgabe innerhalb eines Ziels die Batchverarbeitung verwendet, muss [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bestimmen, ob die Eingaben und Ausgaben für jeden Batch der Elemente aktuell sind. Andernfalls wird das Ziel jedes Mal ausgeführt, wenn es erreicht wird.  
  
 Im folgenden Beispiel wird ein `Target`-Element dargestellt, das ein `Outputs`-Attribut mit der Notation %(\<ItemMetaDataName>) enthält. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] unterteilt die `Example`-Elementliste basierend auf den `Color`-Elementmetadaten in Batches und analysiert die Zeitstempel der Ausgabedateien jedes Batchs. Wenn die Ausgaben eines Batchs nicht aktuell sind, wird das Ziel ausgeführt. Andernfalls wird das Ziel übersprungen.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Ein weiteres Beispiel für die Zielbatchverarbeitung finden Sie unter [Elementmetadaten bei der Zielbatchverarbeitung](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Eigenschaftenfunktionen mit Metadaten  
 Die Batchverarbeitung kann von den Eigenschaftenfunktionen kontrolliert werden, die Metadaten enthalten. Ein auf ein Objekt angewendeter  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 <xref:System.IO.Path.Combine%2A> wird verwendet, um den Stammpfad eines Ordners mit dem Elementpfad einer Kompilierung zu kombinieren.  
  
 Eigenschaftenfunktionen werden möglicherweise nicht innerhalb der Metadatenwerte angezeigt.  Ein auf ein Objekt angewendeter  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 ist nicht zulässig.  
  
 Weitere Informationen zu Eigenschaftenfunktionen finden Sie unter [Eigenschaftenfunktionen](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ItemMetadata-Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)
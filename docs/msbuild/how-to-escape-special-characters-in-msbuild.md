---
title: 'Vorgehensweise: Escapesonderzeichen in MSBuild | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2adf6d94ca2dfa0168a9d694ec2feb83c46e80fe
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Gewusst wie: Escapesonderzeichen in MSBuild
Bestimmte Zeichen haben in Projektdateien [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] eine besondere Bedeutung. Beispiele für die Zeichen sind Semikolons (;) und Sternchen (*). Eine vollständige Liste dieser Sonderzeichen finden Sie unter [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md).  
  
 Um diese Sonderzeichen als Literale in einer Projektdatei zu verwenden, müssen sie mit der Syntax %*xx* angegeben werden, wobei *xx* den ASCII-Hexadezimalwert des Zeichens darstellt.  
  
## <a name="msbuild-special-characters"></a>MSBuild-Sonderzeichen  
 Ein Beispiel, in dem Sonderzeichen verwendet werden, ist im Attribut `Include` von Elementlisten. Die folgende Liste deklariert z.B. zwei Elemente: `MyFile.cs` und `MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Wenn Sie ein Element, das ein Semikolon im Namen enthält, deklarieren möchten, müssen Sie die Syntax %*xx* verwenden, um das Semikolon zu umgehen und um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] daran zu hindern, zwei separate Elemente zu deklarieren. Das folgende Element umgeht beispielsweise den Semikolon und deklariert ein Element mit dem Namen `MyFile.cs;MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>So verwenden Sie ein MSBuild-Sonderzeichen als Literalzeichen  
  
-   Verwenden Sie die Notation %*xx* anstelle des Sonderzeichens, wobei *xx* den Hexadezimalwert des ASCII-Zeichens darstellt. Wenn Sie ein Sternchen (*) als Literalzeichen verwenden möchten, verwenden Sie z. B. den Wert `%2A`.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [MSBuild-Elemente](../msbuild/msbuild.md) [Items](../msbuild/msbuild-items.md)
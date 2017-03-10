---
title: 'Vorgehensweise: Escapesonderzeichen in MSBuild | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 90f2d3d94d7073d0bc694b020496996db31b342a
ms.lasthandoff: 02/22/2017

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
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)
 [Elemente](../msbuild/msbuild-items.md)

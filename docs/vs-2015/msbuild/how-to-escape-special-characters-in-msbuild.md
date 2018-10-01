---
title: 'Vorgehensweise: Escapesonderzeichen in MSBuild | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a900ebe49e95b512c0f53a5542f0ba8ee238a83f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522898"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Gewusst wie: Escapesonderzeichen in MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Escapesonderzeichen in MSBuild](https://docs.microsoft.com/visualstudio/msbuild/how-to-escape-special-characters-in-msbuild).  
  
  
Bestimmte Zeichen haben in Projektdateien [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] eine besondere Bedeutung. Beispiele für die Zeichen sind Semikolons (;) und Sternchen (*). Eine vollständige Liste dieser Sonderzeichen finden Sie unter [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md).  
  
 Um diese Sonderzeichen als Literale in einer Projektdatei zu verwenden, müssen sie mit der Syntax %*xx* angegeben werden, wobei *xx* den ASCII-Hexadezimalwert des Zeichens darstellt.  
  
## <a name="msbuild-special-characters"></a>MSBuild-Sonderzeichen  
 Ein Beispiel, in dem Sonderzeichen verwendet werden, ist im Attribut `Include` von Elementlisten. Die folgende Liste deklariert z.B. zwei Elemente: `MyFile.cs` und `MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Wenn Sie ein Element, das ein Semikolon im Namen enthält, deklarieren möchten, müssen Sie die Syntax %*xx* verwenden, um das Semikolon zu umgehen und um [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] daran zu hindern, zwei separate Elemente zu deklarieren. Das folgende Element umgeht beispielsweise den Semikolon und deklariert ein Element mit dem Namen `MyFile.cs;MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>So verwenden Sie ein MSBuild-Sonderzeichen als Literalzeichen  
  
-   Verwenden Sie die Notation %*xx* anstelle des Sonderzeichens, wobei *xx* den Hexadezimalwert des ASCII-Zeichens darstellt. Wenn Sie ein Sternchen (*) als Literalzeichen verwenden möchten, verwenden Sie z. B. den Wert `%2A`.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)  (MSBuild-Grundlagen)  
 [MSBuild-Elemente](msbuild.md) [Items](../msbuild/msbuild-items.md)



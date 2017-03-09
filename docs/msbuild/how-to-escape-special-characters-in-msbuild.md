---
title: "Gewusst wie: Escapesonderzeichen in MSBuild | Microsoft Docs"
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
  - "Escapezeichen für Sonderzeichen"
  - "Zeichen, Escapesequenzen"
  - "Escapezeichen"
  - "MSBuild-Sonderzeichen"
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Escapesonderzeichen in MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bestimmte Zeichen haben eine besonderen Bedeutung in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Projektdateien. Beispiele für die Zeichen sind Semikolons (;) und Sternchen (*). Eine vollständige Liste dieser Sonderzeichen, finden Sie unter [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md).  
  
 Um diese Sonderzeichen als Literale in einer Projektdatei zu verwenden, müssen sie mit der Syntax % angegeben werden*Xx*, wobei *Xx* den ASCII-Hexadezimalwert des Zeichens darstellt.  
  
## <a name="msbuild-special-characters"></a>MSBuild-Sonderzeichen  
 Ein Beispiel bei Sonderzeichen verwendet werden, ist das `Include` -Attribut des Elements aufgeführt. Die folgende Liste deklariert z. B. zwei Elemente: `MyFile.cs` und `MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Wenn Sie ein Element, das ein Semikolon im Namen enthält, deklarieren möchten, müssen, verwenden Sie den %*Xx* Syntax, um das Semikolon mit Escapezeichen versehen und zu verhindern, dass [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aus zwei verschiedene Elemente deklariert. Zum Beispiel das folgende Element versieht das Semikolon und deklariert eine mit dem Namen `MyFile.cs;MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Verwenden Sie ein MSBuild-Sonderzeichen als Literalzeichen  
  
-   Verwenden Sie die Notation %*Xx* anstelle des Sonderzeichens, wobei *Xx* den Hexadezimalwert des ASCII-Zeichens darstellt. Wenn Sie ein Sternchen (*) als Literalzeichen verwenden möchten, verwenden Sie z. B. den Wert `%2A`.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild-Konzepte](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild1.md)
 [Elemente](../msbuild/msbuild-items.md)
---
title: 'Vorgehensweise: Escapesonderzeichen in MSBuild | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752f4c6535f498b074d2c85b4b7cb6e9870ea862
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853939"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Vorgehensweise: Escapesonderzeichen in MSBuild

Bestimmte Zeichen haben in Projektdateien [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] eine besondere Bedeutung. Beispiele für die Zeichen sind Semikolons (`;`) und Sternchen (`*`). Eine vollständige Liste dieser Sonderzeichen finden Sie unter [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md).

Um diese Sonderzeichen als Literale in einer Projektdatei zu verwenden, müssen sie mit der Syntax `%<xx>` angegeben werden, wobei `<xx>` den ASCII-Hexadezimalwert des Zeichens darstellt.

## <a name="msbuild-special-characters"></a>MSBuild-Sonderzeichen

Ein Beispiel, in dem Sonderzeichen verwendet werden, ist im Attribut `Include` von Elementlisten. Die folgende Liste deklariert z. B. zwei Elemente: *MyFile.cs* und *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Wenn Sie ein Element deklarieren möchten, das ein Semikolon im Namen enthält, müssen Sie die Syntax `%<xx>` verwenden, um das Semikolon zu umgehen und um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] daran zu hindern, zwei separate Elemente zu deklarieren. Das folgende Element umgeht beispielsweise den Semikolon und deklariert ein Element mit dem Namen `MyFile.cs;MyClass.cs`.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Sie können auch eine [Eigenschaftenfunktion](../msbuild/property-functions.md) verwenden, um Zeichenfolgen mit Escapezeichen zu versehen. Dies ist beispielsweise äquivalent zu dem Beispiel oben.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>So verwenden Sie ein MSBuild-Sonderzeichen als Literalzeichen

Verwenden Sie die Notation `%<xx>` anstelle des Sonderzeichens, wobei `<xx>` den Hexadezimalwert des ASCII-Zeichens darstellt. Wenn Sie ein Sternchen (`*`) als Literalzeichen verwenden möchten, verwenden Sie z.B. den Wert `%2A`.

## <a name="see-also"></a>Siehe auch
[MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)  
[MSBuild](../msbuild/msbuild.md)  
[Elemente](../msbuild/msbuild-items.md)

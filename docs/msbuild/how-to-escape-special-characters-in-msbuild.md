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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 955739372605b9e4f9fe58f73669322e2724de31
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595006"
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
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Elemente](../msbuild/msbuild-items.md)

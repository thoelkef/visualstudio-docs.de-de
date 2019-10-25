---
title: Einführung in IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 0d0d681c59935bbbb4591438f538d0c800cba489
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653204"
---
# <a name="get-started-with-microsoft-intellitest"></a>Erste Schritte mit Microsoft IntelliTest

* Wenn Sie zum ersten Mal mit IntelliTest arbeiten:
  * Sehen Sie sich dieses [Channel 9-Video](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest) an
  * Lesen Sie diese [Übersicht im MSDN-Magazin](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * Lesen Sie unsere [Dokumentation](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Stellen Sie Ihre Fragen unter [Stapelüberlauf](http://stackoverflow.com/questions/tagged/intellitest).
* Lesen Sie den Rest dieses Referenzhandbuchs
* Drucken Sie diese Seite als Kurzreferenz aus

## <a name="important-attributes"></a>Wichtige Attribute

* [PexClass](attribute-glossary.md#pexclass) kennzeichnet einen Typ, der **PUT** enthält
* [PexMethod](attribute-glossary.md#pexmethod) markiert ein **PUT**-Objekt
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) kennzeichnet einen Parameter, der nicht NULL ist

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) bindet ein Testprojekt an ein Projekt an
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) gibt an, dass eine Assembly instrumentiert werden soll

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> Wichtige statische Hilfsklassen

* [PexAssume](static-helper-classes.md#pexassume) wertet Annahmen aus (Eingabefilterung)
* [PexAssert](static-helper-classes.md#pexassert) wertet Assertionen aus
* [PexChoose](static-helper-classes.md#pexchoose) generiert neue Optionen (zusätzliche Eingaben)
* [PexObserve](static-helper-classes.md#pexobserve) protokolliert Live-Werte für die generierten Tests

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>Sie möchten Feedback geben?

Posten Sie Ihre Ideen und Featureanfragen in der [Entwicklercommunity](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

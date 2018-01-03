---
title: "Attributglossar | Microsoft IntelliTest Test-Tool für Entwickler | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Attribute glossary
ms.assetid: 557C7869-48BE-4B82-9563-1FF356ABACDB
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 9e3fe1108c316eefe7993a7f564cfd89f4f123dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="attribute-glossary"></a>Attributglossar

## <a name="attributes-by-namespace"></a>Attribute nach Namespace

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)<p />

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)<p />

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)<p />

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)<p />

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Dieses Attribut gibt an, dass der zugehörige Wert nicht **NULL** sein darf. Es kann folgenden Objekten zugeordnet werden:

* einem **Parameter** einer parametrisierten Testmethode

  ```
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* einem **Feld**

  ```
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* einem **Typ**

  ```
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Es kann auch an eine Testassembly, Testfixierung oder Testmethode angefügt werden; in diesem Fall müssen die ersten Argumente angeben, für welches Feld oder welchen Typ die Annahmen gelten. Wenn das Attribut für einen Typ gilt, dann gilt es für alle Felder mit diesem formalen Typ.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Dieses Attribut markiert eine Klasse, die *Durchsuchungsvorgänge* enthält. Dies entspricht dem **TestClassAttribute** von MSTest (oder dem **TestFixtureAttribute** von NUnit). Dieses Attribut ist optional.

Die mit [PexClass](#pexclass) markierten Klassen müssen *standardmäßig konstruierbar* sein:

* öffentlich exportierter Typ
* Standardkonstruktor
* nicht abstrakt

Wenn die Klasse diese Anforderungen nicht erfüllt, wird ein Fehler gemeldet, und das Durchsuchen schlägt fehl.

Es wird auch dringend empfohlen, diese Klassen **partiell** zu machen, damit IntelliTest neue Tests generieren kann, die Teil der Klasse sind, sich aber in einer separaten Datei befinden. Dieser Ansatz löst aufgrund der [Sichtbarkeit](input-generation.md#visibility) viele Probleme und ist ein übliches Verfahren in C#.

**Zusätzliche Sammlung und Kategorien**:

```
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Angeben des getesteten Typs**:

```
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Die Klasse enthält möglicherweise Methoden, die mit [PexMethod](#pexmethod) versehen wurden. IntelliTest erkennt auch [Einrichtungs- und Löschmethoden](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Dieses Attribut bietet ein Typtupel für die Instanziierung eines [generischen parametrisierten Unittests](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Dieses Attribut kennzeichnet eine Methode als [parametrisierten Unittest](test-generation.md#parameterized-unit-testing).
Die Methode muss sich in einer Klasse befinden, die mit dem [PexClass](#pexclass)-Attribut markiert ist.

IntelliTest generiert herkömmliche, parameterlose Tests, die den [parametrisierten Unittest](test-generation.md#parameterized-unit-testing) mit verschiedenen Parametern aufrufen.

Der parametrisierte Unittest:

* muss eine Instanzmethode sein
* muss für die Testklasse [sichtbar](input-generation.md#visibility) sein, in der die generierten Tests gemäß dem [Einstellungswasserfall](settings-waterfall.md) platziert werden
* kann eine beliebige Anzahl von Parametern annehmen
* kann generisch sein

**Beispiel**

```
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Weitere Informationen](https://msdn.microsoft.com/library/microsoft.pex.framework.pexexplorationattributebase.aspx)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Dieses Attribut kann auf Assemblyebene festgelegt werden, um die Werte der Standardeinstellung für alle Durchsuchungsvorgänge außer Kraft zu setzen.

```
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Dieses Attribut gibt an, dass eine Assembly im aktuellen Testprojekt getestet wird. 

```
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Dieses Attribut wird für eine Assembly verwendet, die instrumentiert werden soll.

**Beispiel**

```
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Dieses Attribut teilt IntelliTest mit, dass ein bestimmter Typ zum Instanziieren (abstrakter) Basistypen oder Schnittstellen verwendet werden kann.

**Beispiel**

```
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Wenn dieses Attribut an eine [PexMethod](#pexmethod) (oder [PexClass](#pexclass)) angefügt wird, ändert sich die Standardlogik von IntelliTest, die angibt, wann der Test fehlschlägt. Der Test wird nicht als fehlgeschlagen angesehen, auch wenn er die angegebene Ausnahme auslöst.

**Beispiel**

Der folgende Test legt fest, dass der Konstruktor von **Stack** eine **ArgumentOutOfRangeException** auslösen kann:

```
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Der Filter wird wie folgt an eine Fixierung angefügt (er kann auch auf Assembly- oder Testebene definiert werden):

```
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Weitere Informationen](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromassemblyattribute.aspx)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Weitere Informationen](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeattribute.aspx)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Weitere Informationen](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeundertestattribute.aspx)

## <a name="got-feedback"></a>Sie möchten Feedback geben?

Posten Sie Ihre Ideen und Clusterfunktion Anforderungen auf **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.

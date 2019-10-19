---
title: 'CA1812: nicht instanziierte interne Klassen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f5a36ee8cffc221d15243ff72e2e71558e867319
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645406"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Nicht instanziierte interne Klassen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel versucht, einen aufzurufenden Konstruktoren des Typs zu suchen, und meldet eine Verletzung, wenn kein-Rückruf gefunden wurde.

 Die folgenden Typen werden von dieser Regel nicht untersucht:

- Werttypen

- Abstrakte Typen

- Enumerationen

- Delegaten

- Vom Compiler ausgegebene Array Typen

- Typen, die nicht instanziiert werden können und die nur `static` (`Shared` in Visual Basic)-Methoden definieren.

  Wenn Sie <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> auf die zu analysierende Assembly anwenden, erfolgt diese Regel nicht für Konstruktoren, die als `internal` gekennzeichnet sind, da Sie nicht erkennen können, ob ein Feld von einer anderen `friend` Assembly verwendet wird.

  Obwohl Sie diese Einschränkung in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Code Analyse nicht umgehen können, tritt die externe, eigenständige FxCop auf internen Konstruktoren auf, wenn jede `friend` Assembly in der Analyse vorhanden ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Typ, oder fügen Sie den Code hinzu, der ihn verwendet. Wenn der Typ nur statische Methoden enthält, fügen Sie einen der folgenden Werte zum-Typ hinzu, um zu verhindern, dass der Compiler einen standardmäßigen öffentlichen Instanzkonstruktor ausgibt:

- Ein privater Konstruktor für Typen, die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] die Versionen 1,0 und 1,1 als Ziel haben.

- Der `static`-Modifizierer (`Shared` in Visual Basic) für Typen, die auf [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] abzielen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Es wird empfohlen, dass Sie diese Warnung in den folgenden Situationen unterdrücken:

- Die-Klasse wird durch spät gebundene Reflektionsmethoden erstellt, z. b. <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Die-Klasse wird automatisch von der Laufzeit oder [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] erstellt. Beispielsweise Klassen, die <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> oder <xref:System.Web.IHttpHandler?displayProperty=fullName> implementieren.

- Die Klasse wird als generischer Typparameter übergeben, der über eine neue Einschränkung verfügt. Im folgenden Beispiel wird z. b. diese Regel erhoben.

  ```csharp
  internal class MyClass
  {
      public DoSomething()
      {
      }
  }
  public class MyGeneric<T> where T : new()
  {
      public T Create()
      {
          return new T();
      }
  }
  // [...]
  MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
  mc.Create();
  ```

  In diesen Fällen wird empfohlen, diese Warnung zu unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)

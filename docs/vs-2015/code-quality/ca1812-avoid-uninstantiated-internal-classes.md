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
ms.openlocfilehash: 401fbfbccfeeeeec5cbdc0e791b110d1b5f0201b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543974"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Nicht instanziierte interne Klassen vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel versucht, einen aufzurufenden Konstruktoren des Typs zu suchen, und meldet eine Verletzung, wenn kein-Rückruf gefunden wurde.

 Die folgenden Typen werden von dieser Regel nicht untersucht:

- Werttypen

- Abstrakte Typen

- Enumerationen

- Delegaten

- Vom Compiler ausgegebene Array Typen

- Typen, die nicht instanziiert werden können und die `static` ( `Shared` nur in Visual Basic)-Methoden definieren.

  Wenn Sie <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> auf die zu analysierende Assembly anwenden, erfolgt diese Regel nicht für Konstruktoren, die als gekennzeichnet sind, `internal` da Sie nicht erkennen können, ob ein Feld von einer anderen `friend` Assembly verwendet wird.

  Obwohl Sie diese Einschränkung bei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] der Code Analyse nicht umgehen können, tritt die externe, eigenständige FxCop-Funktion auf internen Konstruktoren auf, wenn jede `friend` Assembly in der Analyse vorhanden ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Typ, oder fügen Sie den Code hinzu, der ihn verwendet. Wenn der Typ nur statische Methoden enthält, fügen Sie einen der folgenden Werte zum-Typ hinzu, um zu verhindern, dass der Compiler einen standardmäßigen öffentlichen Instanzkonstruktor ausgibt:

- Ein privater Konstruktor für Typen, die auf die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Versionen 1,0 und 1,1 abzielen.

- Der `static` - `Shared` Modifizierer (in Visual Basic) für Typen, die auf abzielen [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Es wird empfohlen, dass Sie diese Warnung in den folgenden Situationen unterdrücken:

- Die-Klasse wird durch spät gebundene Reflektionsmethoden wie erstellt <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> .

- Die-Klasse wird automatisch von der Laufzeit oder erstellt [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Beispielsweise Klassen, die <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> oder implementieren <xref:System.Web.IHttpHandler?displayProperty=fullName> .

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
 [CA1811: Nicht aufgerufenen privaten Code vermeiden.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Nicht verwendete Parameter überprüfen.](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen.](../code-quality/ca1804-remove-unused-locals.md)

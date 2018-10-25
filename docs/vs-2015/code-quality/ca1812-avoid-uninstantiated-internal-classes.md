---
title: 'CA1812: Nicht instanziierte interne Klassen vermeiden. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5236fd2dd4635b88ce82b993ebbc15a25e767df1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899785"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Nicht instanziierte interne Klassen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt.

## <a name="rule-description"></a>Regelbeschreibung
 Mit dieser Regel versucht, einen Aufruf eines Konstruktors den Typ zu finden, und gibt einen Verstoß aus, wenn kein Aufruf gefunden wird.

 Die folgenden Typen werden nicht durch diese Regel überprüft:

- Werttypen

- Abstrakte Typen

- Enumerationen

- Delegaten

- Compilerfehler ausgegebenen Arraytypen

- Typen, die nicht instanziiert werden kann, und definieren `static` (`Shared` in Visual Basic) Methoden nur.

  Wenn Sie anwenden <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> auf die Assembly, die analysiert wird, mit dieser Regel treten nicht für Konstruktoren, die als markiert sind `internal` , da Sie nicht erkennen können, ob ein Feld von einem anderen verwendeten `friend` Assembly.

  Auch wenn Sie diese Einschränkung umgehen, können nicht [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Codeanalyse, die externe eigenständige FxCop treten auf interne Konstruktoren, wenn alle `friend` Assembly in der Analyse vorhanden ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Typ, oder fügen Sie den Code, der verwendet wird. Wenn der Typ nur statische Methoden enthält, fügen Sie eine der folgenden in den Typ aus, um zu verhindern, dass den Compiler einen Standardkonstruktor für die öffentliche Instanz ausgeben:

-   Ein privater Konstruktor für Typen, die auf [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Versionen 1.0 und 1.1.

-   Die `static` (`Shared` in Visual Basic)-Modifizierer für Typen, die auf [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel. Es wird empfohlen, dass Sie diese Warnung in den folgenden Situationen unterdrücken:

- Die Klasse wird durch für spät gebundene Reflektionsmethoden erstellt, wie z. B. <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Die Klasse wird automatisch erstellt, von der Laufzeit oder [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Z. B. Klassen, in denen <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> oder <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Die Klasse wird als ein generischer Typparameter übergeben, die eine neue Einschränkung aufweist. Beispielsweise wird im folgenden Beispiel wird diese Regel ausgelöst.

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

  In diesen Fällen wird empfohlen, dass Sie diese Warnung unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)




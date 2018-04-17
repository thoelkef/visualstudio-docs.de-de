---
title: 'CA1812: Nicht instanziierte interne Klassen vermeiden | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47ddd32dd590523fa4b3bfe4ab2d63951ccf503a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Nicht instanziierte interne Klassen vermeiden
|||  
|-|-|  
|TypeName|AvoidUninstantiatedInternalClasses|  
|CheckId|CA1812|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Instanz eines Typs auf Assemblyebene wird nicht durch Code in der Assembly erstellt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel versucht, einen Aufruf an die Konstruktoren des Typs zu suchen, und einen Verstoß gemeldet, wenn kein Aufruf gefunden wird.  
  
 Die folgenden Typen werden nicht durch diese Regel überprüft:  
  
-   Werttypen  
  
-   Abstrakte Typen  
  
-   Enumerationen  
  
-   Delegaten  
  
-   Compilerfehler ausgegeben Arraytypen  
  
-   Typen, die nicht instanziiert werden kann und für die definiert `static` (`Shared` in Visual Basic) Methoden nur.  
  
 Wenn Sie anwenden <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> auf die Assembly, die analysiert wird, wird diese Regel erfolgt nicht auf Konstruktoren, die als markiert sind `internal` , da Sie nicht erkennen können, ob ein Feld, durch eine andere verwendet wird `friend` Assembly.  
  
 Obwohl Sie diese Einschränkung umgehen, können nicht [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Codeanalyse, die externe eigenständige FxCop treten auf interne Konstruktoren, wenn alle `friend` Assembly ist in der Analyse vorhanden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Typ, oder fügen Sie den Code, der verwendet wird. Wenn der Typ nur statische Methoden enthält, fügen Sie eines der folgenden in den Typ, um zu verhindern, dass den Compiler einen öffentlichen Standardinstanzkonstruktor ausgeben:  
  
-   Ein privater Konstruktor für Typen, die auf [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Versionen 1.0 und 1.1.  
  
-   Die `static` (`Shared` in Visual Basic)-Modifizierer für Typen, die auf [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel. Es wird empfohlen, dass Sie diese Warnung in den folgenden Situationen zu unterdrücken:  
  
-   Die Klasse wird durch spät gebundene Reflektionsmethoden erstellt, z. B. <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.  
  
-   Die Klasse wird von der Runtime automatisch erstellt oder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Z. B. Klassen, in denen <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> oder <xref:System.Web.IHttpHandler?displayProperty=fullName>.  
  
-   Die Klasse wird als ein generischer Typparameter übergeben, die eine neue Einschränkung aufweist. Im folgende Beispiel wird beispielsweise diese Regel ausgelöst.  
  
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
  
 In diesen Fällen wird empfohlen, dass Sie diese Warnung zu unterdrücken.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
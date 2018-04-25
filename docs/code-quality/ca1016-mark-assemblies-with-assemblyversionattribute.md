---
title: 'CA1016: Assemblys mit AssemblyVersionAttribute markieren'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c4f05003fdd05a4dde82d19ba11e47c35666fbc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Assemblys mit AssemblyVersionAttribute markieren
|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Die Assembly keine Versionsnummer.

## <a name="rule-description"></a>Regelbeschreibung
 Die Identität einer Assembly besteht aus den folgenden Informationen:

-   Assemblyname

-   Versionsnummer

-   Kultur

-   Öffentliche Schlüssel (für Assemblys mit starkem Namen).

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwendet die Versionsnummer für die eindeutige Identifizierung einer Assembly und zum Binden an Datentypen in Assemblys mit starkem Namen. Die Versionsnummer wird zusammen mit der Versions- und Herausgeberrichtlinie verwendet. Standardmäßig werden Anwendungen nur mit der Assemblyversion ausgeführt, mit der sie erstellt wurden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie eine Versionsnummer der Assembly mithilfe der <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> Attribut. Weitere Informationen finden Sie im folgenden Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel für Assemblys, die von Drittanbietern oder in einer produktiven Umgebung verwendet werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, die <xref:System.Reflection.AssemblyVersionAttribute> Attribut angewendet.

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Siehe auch
 [Assemblyversionen](/dotnet/framework/app-domains/assembly-versioning) [Vorgehensweise: Erstellen einer Herausgeberrichtlinie](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)
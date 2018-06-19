---
title: 'CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren'
ms.date: 03/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beaef23dd5b3047d1d65b90fdd984dfdedd7e145
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916386"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Assembly enthält eine **ResX**-klassenbasierten Ressource weist jedoch keine der <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> angewendet wird.

## <a name="rule-description"></a>Regelbeschreibung

Die <xref:System.Resources.NeutralResourcesLanguageAttribute> den Ressourcen-Manager von einer app-Standardkultur-Attribut wird. Wenn die Standardkultur Ressourcen in die Hauptassembly der app eingebettet sind und <xref:System.Resources.ResourceManager> hat beim Abrufen von Ressourcen, die das dieselbe Kultur aufweist wie die Standardkultur gehören die <xref:System.Resources.ResourceManager> verwendet automatisch die Ressourcen in die Hauptassembly anstelle der Suche nach einer Satellitenassembly. Dies umgeht den üblichen Assembly Prüfpunkt, verbessert die Leistung der Suche für die erste Ressource geladen und Ihr Workingset reduzieren können.

> [!TIP]
> Finden Sie unter [Verpacken und Bereitstellen von Ressourcen](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) für den Prozess, <xref:System.Resources.ResourceManager> verwendet, um für die Suche nach Ressourcendateien.

## <a name="fix-violations"></a>Beheben von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das Attribut auf die Assembly, und geben Sie die Sprache der Ressourcen der neutralen Kultur.

### <a name="to-specify-the-neutral-language-for-resources"></a>Für Ressourcen die neutrale Sprache angeben.

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.

2. Wählen Sie die **Anwendung** Registerkarte, und wählen Sie dann **Assemblyinformationen**.

   > [!NOTE]
   > Wenn Ihr Projekt eine .NET Standard oder .NET Core ist, wählen Sie die **Paket** Registerkarte.

3. Wählen Sie die Sprache aus der **neutrale Sprache** oder **Assembly neutrale Sprache** Dropdown-Liste.

4. Klicken Sie auf **OK**.

## <a name="when-to-suppress-warnings"></a>Wenn Warnungen unterdrücken

Es ist zulässig, unterdrücken Sie eine Warnung dieser Regel. Allerdings kann die Leistung beim Start beeinträchtigen.

## <a name="see-also"></a>Siehe auch

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Ressourcen in desktop-apps (.NET)](/dotnet/framework/resources/)
- [CA1703 - Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 - Ressource-Zeichenfolge an, die zusammengesetzte Wörter beachtet werden sollten](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
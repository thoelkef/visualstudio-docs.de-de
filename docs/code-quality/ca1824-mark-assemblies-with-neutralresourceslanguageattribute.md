---
title: 'CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren.'
ms.date: 03/29/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40cb2a3674884a9fb4f1449c9afa2e0a2d27050f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808559"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren.

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Assembly enthält eine **ResX**-klassenbasierten Ressource, aber keinen der <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> angewendet wird.

## <a name="rule-description"></a>Regelbeschreibung

Die <xref:System.Resources.NeutralResourcesLanguageAttribute> Attribut informiert den Ressourcen-Manager der Standardkultur einer app. Wenn Ressourcen der Standardkultur in die Hauptassembly der app eingebettet sind und <xref:System.Resources.ResourceManager> wurde zum Abrufen von Ressourcen, die dieselbe Kultur aufweist wie die Standardkultur, gehören die <xref:System.Resources.ResourceManager> verwendet automatisch die Ressourcen in der Hauptassembly anstatt die Suche nach einer Satellitenassembly. Dies umgeht den üblichen Assembly-Test, verbessert die suchleistung für die erste Ressource, die Sie laden möchten, die und können Ihr Workingset reduziert.

> [!TIP]
> Finden Sie unter [Verpacken und Bereitstellen von Ressourcen](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) für den Prozess, <xref:System.Resources.ResourceManager> verwendet, um nach Dateien gesucht.

## <a name="fix-violations"></a>Beheben von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das-Attribut auf die Assembly, und geben Sie die Sprache der Ressourcen der neutralen Kultur.

### <a name="to-specify-the-neutral-language-for-resources"></a>Für Ressourcen der neutralen Sprache an

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.

2. Wählen Sie die **Anwendung** Registerkarte, und wählen Sie dann **Assemblyinformationen**.

   > [!NOTE]
   > Wenn Ihr Projekt ein .NET Standard oder .NET Core-Projekt handelt, wählen Sie die **Paket** Registerkarte.

3. Wählen Sie die Sprache aus der **neutrale Sprache** oder **Assembly neutrale Sprache** Dropdown-Liste.

4. Klicken Sie auf **OK**.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist zulässig, unterdrücken Sie eine Warnung dieser Regel. Allerdings kann die Leistung beim Start beeinträchtigen.

## <a name="see-also"></a>Siehe auch

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Ressourcen in desktop apps (.NET)](/dotnet/framework/resources/)
- [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 - Ressourcenzeichenfolge, die zusammengesetzte Wörter beachtet werden sollten](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
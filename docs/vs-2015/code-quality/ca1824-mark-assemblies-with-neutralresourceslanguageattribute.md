---
title: 'CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: efa328fdff9c357e0183fc2ca80e4d77d4f6782e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661119"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Assembly enthält eine **RESX**-basierte Ressource, aber die <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> nicht darauf angewendet.

## <a name="rule-description"></a>Regelbeschreibung
 Das **NeutralResourcesLanguage** -Attribut informiert den **ResourceManager** über die Sprache, die verwendet wurde, um die Ressourcen der neutralen Kultur für eine Assembly anzuzeigen. Wenn Ressourcen in derselben Kultur wie die neutrale Ressourcen Sprache nachgeschlagen werden, verwendet der **ResourceManager** automatisch die Ressourcen, die sich in der Hauptassembly befinden. Dies geschieht, anstatt nach einer Satellitenassembly zu suchen, die über die aktuelle Benutzeroberflächen Kultur für den aktuellen Thread verfügt. Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern.

## <a name="fixing-violations"></a>Beheben von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Assembly das-Attribut hinzu, und geben Sie die Sprache der Ressourcen der neutralen Kultur an.

## <a name="specifying-the-language"></a>Angeben der Sprache

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>So geben Sie die Sprache der Ressource der neutralen Kultur an

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.

2. Wählen Sie in der linken Navigationsleiste **Anwendung**aus, und klicken Sie dann auf Assemblyinformationen.

3. Wählen Sie im Dialogfeld Assemblyinformationen in der Dropdown Liste **neutrale Sprache** die Sprache aus.

4. Klicken Sie auf **OK**.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist zulässig, eine Warnung aus dieser Regel zu unterdrücken. Allerdings kann sich die Leistung des Starts verringern.

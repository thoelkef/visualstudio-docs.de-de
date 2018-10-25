---
title: 'CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren | Microsoft-Dokumentation'
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
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 13f635398ecab7c0bd9436a86a43a15d4908b163
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892596"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Assembly enthält eine **ResX**-klassenbasierten Ressource, aber keinen der <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> angewendet wird.

## <a name="rule-description"></a>Regelbeschreibung
 Die **NeutralResourcesLanguage** Attribut informiert die **ResourceManager** der Sprache, die verwendet wurde, um die Ressourcen der neutralen Kultur für eine Assembly angezeigt werden soll. Wenn sie Ressourcen in der gleichen Kultur als neutrale Sprachressourcen, sucht die **ResourceManager** verwendet automatisch die Ressourcen, die in der Hauptassembly gespeichert sind. Dies wird anstelle der Suche nach einer Satellitenassembly mit der aktuellen Benutzeroberflächenkultur für den aktuellen Thread. Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern.

## <a name="fixing-violations"></a>Beheben von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das-Attribut auf die Assembly, und geben Sie die Sprache der Ressourcen der neutralen Kultur.

## <a name="specifying-the-language"></a>Angeben der Sprache

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Die Sprache der Ressource der neutralen Kultur angeben

1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.

2.  Wählen Sie in der linken Navigationsleiste **Anwendung**, und klicken Sie dann auf **Assemblyinformationen**.

3.  In der **Assemblyinformationen** Dialogfeld wählen die Sprache aus der **neutrale Sprache** Dropdown-Liste.

4.  Klicken Sie auf **OK**.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist zulässig, unterdrücken Sie eine Warnung dieser Regel. Allerdings kann die startleistung verringern.




---
title: 'CA1824: Assemblys mit NeutralResourcesLanguageAttribute markieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6c9d4da3becaa6831f30a5cc6c72d1f0b3b70eea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 Die **NeutralResourcesLanguage** -Attribut wird der **ResourceManager** der Sprache, die verwendet wurde, um die Ressourcen der neutralen Kultur für eine Assembly angezeigt. Wenn sie Ressourcen in das dieselbe Kultur aufweist wie die der neutralen Ressourcensprache sucht die **ResourceManager** verwendet automatisch die Ressourcen, die in die Hauptassembly befinden. Dies geschieht anstelle der Suche nach einer Satellitenassembly, die die aktuelle Benutzeroberflächenkultur für den aktuellen Thread verfügt. Auf diese Weise wird die Suchleistung für die erste zu ladende Ressource verbessert und Ihr Workingset kann sich verkleinern.  
  
## <a name="fixing-violations"></a>Korrigieren von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das Attribut auf die Assembly, und geben Sie die Sprache der Ressourcen der neutralen Kultur.  
  
## <a name="specifying-the-language"></a>Angeben der Sprache  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Die Sprache für die Ressourcen der neutralen Kultur angeben  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Wählen Sie in der linken Navigationsleiste **Anwendung**, und klicken Sie dann auf **Assemblyinformationen**.  
  
3.  In der **Assemblyinformationen** Dialogfeld wählen die Sprache aus der **neutrale Sprache** Dropdown-Liste.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Es ist zulässig, unterdrücken Sie eine Warnung dieser Regel. Allerdings kann die Leistung beim Start verringern.
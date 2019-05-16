---
title: 'Vorgehensweise: Festlegen von CLR-Attribute für ein Element | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9af25934a40c01c6b4cfd48dcd7419bddf322d3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698027"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Vorgehensweise: Festlegen von CLR-Attributen für ein Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Benutzerdefinierte Attribute sind spezielle Attribute, die Domänenelemente, Formen, Konnektoren und Diagrammen hinzugefügt werden können. Sie können alle Attribute, die von erbt Hinzufügen der `System.Attribute` Klasse.  
  
### <a name="to-add-a-custom-attribute"></a>Ein benutzerdefiniertes Attribut hinzufügen  
  
1. In der **DSL-Explorer**, wählen Sie das Element, dem Sie ein benutzerdefiniertes Attribut hinzufügen möchten.  
  
2. In der **Eigenschaften** neben der **benutzerdefinierte Attribute** -Eigenschaft, klicken Sie auf die Schaltfläche zum Durchsuchen (**...** ) Symbol.  
  
     Die **Attribute bearbeiten** Dialogfeld wird geöffnet.  
  
3. In der **Namen** Spalte, klicken Sie auf  **\<Attribut hinzufügen >** und geben Sie den Namen eines Attributs. Drücken Sie die EINGABETASTE.  
  
4. Linie unter dem Attributnamen zeigt die Klammern. Geben Sie in dieser Zeile einen Parametertyp für das Attribut (z. B. `string`), und drücken Sie dann die EINGABETASTE.  
  
5. In der **Namenseigenschaft** Spalte Geben Sie einen geeigneten Namen, z. B. `MyString`.  
  
6. Klicken Sie auf **OK**.  
  
     Die **benutzerdefinierte Attribute** Eigenschaft zeigt jetzt das Attribut im folgenden Format:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`  
  
## <a name="see-also"></a>Siehe auch  
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

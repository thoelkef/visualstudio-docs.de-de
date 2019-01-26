---
title: 'Vorgehensweise: Festlegen von CLR-Attributen für ein Element'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 54b4340fe72552f3287a5c6ebec55c9c9d326ac1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932271"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Vorgehensweise: Festlegen von CLR-Attributen für ein Element
Benutzerdefinierte Attribute sind spezielle Attribute, die Domänenelemente, Formen, Konnektoren und Diagrammen hinzugefügt werden können. Sie können alle Attribute, die von erbt Hinzufügen der `System.Attribute` Klasse.

### <a name="to-add-a-custom-attribute"></a>Ein benutzerdefiniertes Attribut hinzufügen

1.  In der **DSL-Explorer**, wählen Sie das Element, dem Sie ein benutzerdefiniertes Attribut hinzufügen möchten.

2.  In der **Eigenschaften** neben der **benutzerdefinierte Attribute** -Eigenschaft, klicken Sie auf die Schaltfläche zum Durchsuchen (**...** ) Symbol.

     Die **Attribute bearbeiten** Dialogfeld wird geöffnet.

3.  In der **Namen** Spalte, klicken Sie auf  **\<Attribut hinzufügen >** und geben Sie den Namen eines Attributs. Drücken Sie die EINGABETASTE.

4.  Linie unter dem Attributnamen zeigt die Klammern. Geben Sie in dieser Zeile einen Parametertyp für das Attribut (z. B. `string`), und drücken Sie dann die EINGABETASTE.

5.  In der **Namenseigenschaft** Spalte Geben Sie einen geeigneten Namen, z. B. `MyString`.

6.  Klicken Sie auf **OK**.

     Die **benutzerdefinierte Attribute** Eigenschaft zeigt jetzt das Attribut im folgenden Format:

     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
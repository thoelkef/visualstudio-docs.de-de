---
title: 'Gewusst wie: Festlegen von CLR-Attributen für ein Element'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1609b92e631abdaba34a18bd32d4fc6d892f7cd7
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966790"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Gewusst wie: Festlegen von CLR-Attributen für ein Element
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

     `[` *AttributeName* `(` *ParameterName* `=` *Typ* `)]`

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
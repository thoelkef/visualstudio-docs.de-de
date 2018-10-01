---
title: 'Vorgehensweise: Festlegen von CLR-Attribute für ein Element | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: afcbadd7c7b3a18c94228e7221eda32b7117a2ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509380"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Gewusst wie: Festlegen von CLR-Attributen für ein Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Festlegen von CLR-Attribute für ein Element](https://docs.microsoft.com/visualstudio/modeling/how-to-set-clr-attributes-on-an-element).  
  
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
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)




---
title: 'Gewusst wie: Festlegen von CLR-Attributen für ein Element | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662543"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Gewusst wie: Festlegen von CLR-Attributen für ein Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Benutzerdefinierte Attribute sind spezielle Attribute, die Domänen Elementen, Formen, Connectors und Diagrammen hinzugefügt werden können. Sie können beliebige Attribute hinzufügen, die von der- `System.Attribute` Klasse erben.

### <a name="to-add-a-custom-attribute"></a>Hinzufügen eines benutzerdefinierten Attributs

1. Wählen Sie im **DSL-Explorer**das Element aus, dem Sie ein benutzerdefiniertes Attribut hinzufügen möchten.

2. Klicken Sie im **Eigenschaften** Fenster neben der Eigenschaft **benutzerdefinierte Attribute** auf das Symbol zum Durchsuchen (**..**.).

     Das Dialogfeld **Attribute bearbeiten** wird geöffnet.

3. Klicken Sie in der Spalte **Name** auf, **\<add attribute>** und geben Sie den Namen des Attributs ein. Drücken Sie die EINGABETASTE.

4. Die Zeile unter dem Attributnamen zeigt Klammern an. Geben Sie in dieser Zeile einen Parametertyp für das Attribut ein (z. b. `string` ), und drücken Sie dann die EINGABETASTE.

5. Geben Sie in der Spalte **Name-Eigenschaft** einen geeigneten Namen ein, z `MyString` . b..

6. Klicken Sie auf **OK**.

     Die Eigenschaft **benutzerdefinierte Attribute** zeigt nun das Attribut im folgenden Format an:

     `[`*AttributeName* `(` *Parameter Name* `=` *Typ*`)]`

## <a name="see-also"></a>Weitere Informationen
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

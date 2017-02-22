---
title: "Gewusst wie: Festlegen von CLR-Attributen f&#252;r ein Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.EditAttributesDialog"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, benutzerdefinierte Attribute"
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 19
caps.handback.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Gewusst wie: Festlegen von CLR-Attributen f&#252;r ein Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Benutzerdefinierte Attribute sind spezielle Attribute, die Domänenelemente, Formen, Connectors und Diagramme hinzugefügt werden können. Sie können jedes Attribut, das von erbt Hinzufügen der `System.Attribute` Klasse.  
  
### <a name="to-add-a-custom-attribute"></a>So fügen Sie ein benutzerdefiniertes Attribut hinzu  
  
1.  In der **Explorer für DSL**, wählen Sie das Element, dem Sie ein benutzerdefiniertes Attribut hinzufügen möchten.  
  
2.  In der **Eigenschaften** neben der **benutzerdefinierte Attribute** -Eigenschaft, klicken Sie auf die Schaltfläche zum Durchsuchen (**...**) Symbol ".  
  
     Die **Attribute bearbeiten** Dialogfeld wird geöffnet.  
  
3.  In den **Namen** Spalte, klicken Sie auf **\< attributhinzufügen>** und geben Sie den Namen des Attributs. Drücken Sie die EINGABETASTE.  
  
4.  Die Linie unter dem Namen des Attributs zeigt Klammern. Geben Sie auf diese Zeile Parametertyp für das Attribut (z. B. `string`), und drücken Sie dann die EINGABETASTE.  
  
5.  In der **Namenseigenschaft** Spalte Geben Sie einen passenden Namen, z. B. `MyString`.  
  
6.  Klicken Sie auf **OK**.  
  
     Die **benutzerdefinierte Attribute** Eigenschaft zeigt jetzt das Attribut im folgenden Format:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *Typ* `)]`  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)
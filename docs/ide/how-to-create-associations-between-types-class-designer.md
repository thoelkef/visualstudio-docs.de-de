---
title: "How to: Create Associations Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.associationline"
helpviewer_keywords: 
  - "types [Visual Studio], associations"
  - "association lines, defining (Class Designer)"
  - "defining association lines (Class Designer)"
  - "associations, types"
  - "association lines"
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create Associations Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Anhand von Assoziationslinien im Klassen\-Designer ist zu erkennen, in welcher Beziehung Klassen in einem Diagramm stehen.  Eine Assoziationslinie stellt eine Klasse dar, die der Typ einer Eigenschaft oder eines Felds einer anderen Klasse im Projekt ist.  In der Regel dienen Assoziationslinien zur Darstellung der wichtigsten Beziehungen zwischen Klassen im Projekt.  
  
 Sie können alle Felder und Eigenschaften als Assoziationen anzuzeigen. Je nachdem, welche Elemente im Diagramm hervorgehoben werden sollen, ist jedoch sinnvoller, nur wichtige Member als Assoziationen anzeigen. \(Sie können weniger wichtige Member als reguläre Member anzeigen oder alle ausblenden.\)  
  
> [!NOTE]
>  Der Klassen\-Designer unterstützt nur Assoziationen in eine Richtung.  
  
### So definieren Sie im Klassendiagramm eine Assoziationslinie  
  
1.  Wählen Sie im Werkzeugkasten unter "Klassen\-Designer" die Option **Zuordnung** aus.  
  
2.  Zeichnen Sie eine Linie zwischen den beiden Formen, die Sie mithilfe einer Assoziation miteinander verbinden möchten.  
  
     In der ersten Klasse wird eine neue Eigenschaft erstellt.  Diese Eigenschaft wird als Assoziationslinie \(nicht als Eigenschaft in einem Depot in der Form\) mit einem Standardnamen angezeigt.  Der zugehörige Typ ist die Form, auf die die Assoziationslinie weist.  
  
### So ändern Sie den Namen einer Assoziation  
  
-   Klicken Sie auf der Diagrammoberfläche auf die Bezeichnung der Assoziationslinie, und geben Sie eine neue Bezeichnung ein.  
  
 – oder –  
  
1.  Klicken Sie auf die Form, in der die als Assoziation angezeigte Eigenschaft enthalten ist.  
  
     Die Form erhält den Fokus, und die zugehörigen Member werden im Klassendetailsfenster und im Eigenschaftenfenster angezeigt.  
  
2.  Bearbeiten Sie nun entweder im Klassendetailsfenster oder im Eigenschaftenfenster das Namensfeld der Eigenschaft, und drücken Sie die EINGABETASTE.  
  
     Der Name wird im Fenster **Klassendetails**, auf der Assoziationslinie, im Eigenschaftenfenster und im Code aktualisiert.  
  
## Siehe auch  
 [How to: Change Between Member Notation and Association Notation \(Class Designer\)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)
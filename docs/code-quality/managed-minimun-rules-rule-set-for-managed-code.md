---
title: "Regelsatz f&#252;r verwaltete Mindestregeln f&#252;r verwalteten Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
caps.handback.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Regelsatz f&#252;r verwaltete Mindestregeln f&#252;r verwalteten Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die verwalteten Mindestregeln konzentrieren sich auf die wichtigsten Probleme im Code, darunter potenzielle Sicherheitslücken, Abstürze der Anwendung und andere wichtige Logik\- und Entwurfsfehler.  Sie sollten diesen Regelsatz in alle benutzerdefinierten Regelsätze einbinden, die Sie für Ihre Projekte erstellen.  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
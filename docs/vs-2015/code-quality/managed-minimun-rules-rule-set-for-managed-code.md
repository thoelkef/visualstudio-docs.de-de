---
title: Legen Sie die Regel für verwaltete Mindestregeln für verwalteten Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cca9670f65ef517a4697fc0752c65cbafbaa3b16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512689"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Regelsatz für verwaltete Mindestregeln für verwalteten Code](https://docs.microsoft.com/visualstudio/code-quality/managed-minimun-rules-rule-set-for-managed-code).  
  
Die verwaltete Mindestregeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, einschließlich potenzieller Sicherheitslücken, Anwendungsabstürze und anderen wichtigen Logik- und Designfehlern. Sie sollten diesen Regelsatz in alle benutzerdefinierten Regelsätze einbinden, die Sie für Ihre Projekte erstellen.  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen müssen gelöscht werden können.|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen des Gleichheitsoperators beim Überschreiben von ValueType.Equals|




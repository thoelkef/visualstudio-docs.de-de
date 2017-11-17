---
title: 'CA2004: Aufrufe an GC zu entfernen. Der KeepAlive | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edb47391872da6754e39a27d2e8a50dc61293af1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Aufrufe an GC.KeepAlive entfernen
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Kategorie|Microsoft.Reliability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Klassen verwenden `SafeHandle` , aber dennoch enthält Aufrufe von `GC.KeepAlive`.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn Sie konvertieren, `SafeHandle` Verwendung "," entfernen Sie alle Aufrufe `GC.KeepAlive` (Objekt). In diesem Fall sollten Klassen nicht haben Aufrufen `GC.KeepAlive`, vorausgesetzt, sie verfügen nicht über einen Finalizer, sondern beruhen auf `SafeHandle` das OS-Handle für diese abgeschlossen.  Obwohl die Kosten für einen Aufruf von `GC.KeepAlive` möglicherweise unerheblich, gemessen an Leistung, das Gefühl, die einen Aufruf von `GC.KeepAlive` erforderlich oder ausreichend, um eine Lebensdauer zu lösen, Problem, das möglicherweise nicht mehr vorhanden ist der Code schwieriger zu, verwalten.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Entfernen Sie Aufrufe von `GC.KeepAlive`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können diese Warnung unterdrücken, nur dann, wenn er nicht in konvertiert technisch korrekt ist `SafeHandle` Nutzung in Ihrer Klasse.
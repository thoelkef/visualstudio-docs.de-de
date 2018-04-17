---
title: 'CA2004: Aufrufe an GC zu entfernen. Der KeepAlive | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d25c42202f7df2214295af4e3d1a448266cfa6cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
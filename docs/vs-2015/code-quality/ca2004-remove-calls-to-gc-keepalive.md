---
title: 'CA2004: Entfernen Sie die Aufrufe von GC. KeepAlive | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e34a8e7d4860a599155554410e13df5a6eb3bfe1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672496"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Aufrufe an GC.KeepAlive entfernen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Klassen verwenden `SafeHandle`, enthalten jedoch weiterhin Aufrufe `GC.KeepAlive`.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Sie in `SafeHandle` Verwendung von umrechnen, entfernen Sie alle Aufrufe an `GC.KeepAlive` (-Objekt). In diesem Fall müssen Klassen `GC.KeepAlive` nicht über einen Finalizer verfügen, sondern auf `SafeHandle`, um das Betriebssystem Handle für Sie abzuschließen.  Obwohl die Kosten für die Beibehaltung eines Aufrufes von `GC.KeepAlive` aufgrund der Leistung vernachlässigbar sein können, ist der Eindruck, dass ein aufrufender `GC.KeepAlive` entweder notwendig oder ausreichend ist, um ein Lebensdauer Problem zu beheben, das möglicherweise nicht mehr vorhanden ist, die Verwaltung des Codes erschwert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie Aufrufe an `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können diese Warnung nur unterdrücken, wenn es nicht technisch korrekt ist, in `SafeHandle` Verwendung in ihrer Klasse zu konvertieren.

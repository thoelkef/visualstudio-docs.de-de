---
title: 'CA2004: Entfernen Sie Aufrufe von GC. KeepAlive | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e75ab22212945e5a6b4465e1e1f64ca48a9daa4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957347"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Aufrufe an GC.KeepAlive entfernen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Klassen geben mit `SafeHandle` , aber dennoch enthält Aufrufe von `GC.KeepAlive`.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Sie zum Konvertieren `SafeHandle` Nutzung, entfernen Sie alle Aufrufe `GC.KeepAlive` (Objekt). In diesem Fall Klassen dürfen keine aufzurufende `GC.KeepAlive`, vorausgesetzt, sie haben keinen Finalizer, sondern basieren auf `SafeHandle` das Betriebssystemhandle für diese durchführen.  Obwohl die Kosten für einen Aufruf von `GC.KeepAlive` möglicherweise unerheblich, wie die Wahrnehmung der Leistung gemessen, die einen Aufruf von `GC.KeepAlive` erforderlich oder ausreichend, um eine Lebensdauer zu lösen, Problem, das möglicherweise nicht mehr vorhanden. Dadurch wird der Code schwieriger zu, verwalten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie Aufrufe von `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können diese Warnung unterdrücken, nur dann, wenn er nicht technisch korrekt zu konvertieren ist `SafeHandle` Nutzung in Ihrer Klasse.

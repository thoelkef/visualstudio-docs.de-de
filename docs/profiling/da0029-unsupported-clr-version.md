---
title: 'DA0029: Nicht unterstützte CLR-Version | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbc0bfcdb49557e56711b60dca11977a3504d907
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777514"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nicht unterstützte CLR-Version

|||
|-|-|
|Regel-ID|DA0029|
|Kategorie|Verwendung der Profilerstellungstools|
|Profilerstellungsmethode|Profilerstellung mithilfe der Befehlszeile|
|Meldung|Während der Sammlung wurde eine nicht unterstützte CLR-Version erkannt. Verwaltete Symbole wurden möglicherweise nicht ordnungsgemäß aufgelöst.|
|Regeltyp|Information|

## <a name="cause"></a>Ursache
 Sie versuchen, das Profil für eine Anwendung zu erstellen, die [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] verwendet, was nicht von den Profilerstellungstools unterstützt wird.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Warnung tritt auf, da die Profilerstellungstools keine Symbole für den verwalteten Code auflösen können, der in der Anwendung ausgeführt wird. Die Profilerstellungstools können keine verwalteten Codesymbole für Anwendungen auflösen, die [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] ausführen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Keine

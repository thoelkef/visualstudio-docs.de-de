---
title: Leistungsregeln für Speicher und Auslagerung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f779a050c334e8f61d6d3711ed2be2a7b087e72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896685"
---
# <a name="memory-and-paging-performance-rules"></a>Leistungsregeln für Speicher und Paging
Die Leistungsregeln in der Speicher- und Auslagerungskategorie identifiziert die Auslagerungsaktivität in einer Profilerstellung, die Anwendungsleistung und -reaktionsfähigkeit beeinträchtigen kann.

|||
|-|-|
|[DA0014: Äußerst hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Im Verlauf der Profilerstellung ist ein hohes Maß an Auslagerung von aktivem Speicher auf und vom Datenträger aufgetreten. Solch hohe Auslagerungsraten wirken sich in der Regel negativ auf Leistung und Reaktionszeit der Anwendung aus. Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten. Sie müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigen. Versuchen Sie, die Profilerstellung erneut auf einem Computer auszuführen, der über mehr Arbeitsspeicher verfügt. Diese Regel wird ausgelöst, wenn die Auslagerungsaktivität den oberen Schwellenwert der Regel DA0017 überschreitet.|
|[DA0017: Hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Im Verlauf der Profilerstellung ist ein relativ hohes Maß an Auslagerung von aktivem Speicher auf den und von dem Datenträger aufgetreten. Solch hohe Auslagerungsraten wirken sich in der Regel negativ auf Leistung und Reaktionszeit der Anwendung aus. Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten. Sie müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigen. Versuchen Sie, die Profilerstellung erneut auf einem Computer auszuführen, der über mehr Arbeitsspeicher verfügt.|
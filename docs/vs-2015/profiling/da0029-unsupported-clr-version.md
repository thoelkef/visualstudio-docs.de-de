---
title: 'DA0029: Nicht unterstützte CLR-Version | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 532427618f476e1e187d8a1c88749810f9d157c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803539"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nicht unterstützte CLR-Version
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-Id | DA0029 |  
| Kategorie | Verwendung der Profilerstellungstools |  
| Profilerstellungsmethode | Profilerstellung über die Befehlszeile |  
| Nachricht | Eine nicht unterstützte CLR-Version wurde während der Sammlung erkannt. Verwaltete Symbole wurden möglicherweise nicht ordnungsgemäß aufgelöst.|  
| Regeltyp | Informationen. |  
  
## <a name="cause"></a>Ursache  
 Sie versuchen, das Profil für eine Anwendung zu erstellen, die [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] verwendet, was nicht von den Profilerstellungstools unterstützt wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Warnung tritt auf, da die Profilerstellungstools keine Symbole für den verwalteten Code auflösen können, der in der Anwendung ausgeführt wird. Die Profilerstellungstools können keine verwalteten Codesymbole für Anwendungen auflösen, die [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] ausführen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Keine

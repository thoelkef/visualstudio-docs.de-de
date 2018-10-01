---
title: 'DA0029: Nicht unterstützte CLR-Version | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df5deda533c21033d26af4b8dc08d98a5dafc583
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509017"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nicht unterstützte CLR-Version
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DA0029: nicht unterstützte CLR-Version](https://docs.microsoft.com/visualstudio/profiling/da0029-unsupported-clr-version).  
  
Regel-Id | DA0029 |  
| Kategorie | Verwendung der Profilerstellungstools |  
| Profilerstellungsmethode | Profilerstellung über die Befehlszeile |  
| Nachricht | Eine nicht unterstützte CLR-Version wurde während der Sammlung erkannt. Verwaltete Symbole werden ggf. nicht richtig aufgelöst. |  
| Regeltyp | Informationen. |  
  
## <a name="cause"></a>Ursache  
 Sie versuchen, das Profil für eine Anwendung zu erstellen, die [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] verwendet, was nicht von den Profilerstellungstools unterstützt wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Warnung tritt auf, da die Profilerstellungstools keine Symbole für den verwalteten Code auflösen können, der in der Anwendung ausgeführt wird. Die Profilerstellungstools können keine verwalteten Codesymbole für Anwendungen auflösen, die [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] ausführen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Keine




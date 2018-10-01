---
title: Leistungsregeln für Speicher und Auslagerung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e9512fefc13dccebdb0a930ea6000edcbbd8f7a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511264"
---
# <a name="memory-and-paging-performance-rules"></a>Leistungsregeln für Speicher und Auslagerung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Speicher und Auslagerung von Leistungsregeln](https://docs.microsoft.com/visualstudio/profiling/memory-and-paging-performance-rules).  
  
Die Leistungsregeln in der Speicher- und Auslagerungskategorie identifiziert die Auslagerungsaktivität in einer Profilerstellung, die Anwendungsleistung und -reaktionsfähigkeit beeinträchtigen kann.  
  
|||  
|-|-|  
|[DA0014: Äußerst hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Im Verlauf der Profilerstellung ist ein hohes Maß an Auslagerung von aktivem Speicher auf und vom Datenträger aufgetreten. Solch hohe Auslagerungsraten wirken sich in der Regel negativ auf Leistung und Reaktionszeit der Anwendung aus. Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten. Sie müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigen. Versuchen Sie, die Profilerstellung erneut auf einem Computer auszuführen, der über mehr Arbeitsspeicher verfügt. Diese Regel wird ausgelöst, wenn die Auslagerungsaktivität den oberen Schwellenwert der Regel DA0017 überschreitet.|  
|[DA0017: Hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Im Verlauf der Profilerstellung ist ein relativ hohes Maß an Auslagerung von aktivem Speicher auf den und von dem Datenträger aufgetreten. Solch hohe Auslagerungsraten wirken sich in der Regel negativ auf Leistung und Reaktionszeit der Anwendung aus. Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten. Sie müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigen. Versuchen Sie, die Profilerstellung erneut auf einem Computer auszuführen, der über mehr Arbeitsspeicher verfügt.|




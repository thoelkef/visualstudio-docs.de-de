---
title: Logische Operatoren in Suchausdrücken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cf55bbdc025b4aabd13f7ded72c2ea69386a61b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510795"
---
# <a name="logical-operators-in-search-expressions"></a>Logische Operatoren in Suchausdrücken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [logische Operatoren in Suchausdrücken](https://docs.microsoft.com/visualstudio/ide/logical-operators-in-search-expressions).  
  
Mithilfe von logischen Operatoren können Sie Ihre Suche nach Inhalten eingrenzen, indem Sie aus einfachen Suchausdrücken komplexere erstellen. Wie in der folgenden Tabelle dargestellt, kann mit logischen Operatoren angegeben werden, wie viele Suchausdrücke in einer Suchabfrage kombiniert werden sollen.  
  
> [!IMPORTANT]
>  Sie müssen logische Operatoren in Großbuchstaben eingeben, damit sie von der Suchmaschine erkannt werden.  
  
|Suchen nach|Mit|Beispiel|Ergebnis|  
|-------------------|---------|-------------|------------|  
|Beide Begriffe im gleichen Thema|UND|dib UND palette|Themen, die sowohl „Dib“ als auch „Palette“ enthalten.|  
|Einer der Begriffe in einem Thema|ODER|Raster ODER Vektor|Themen, die entweder „Raster“ oder „Vektor“ enthalten.|  
|Erster Begriff ohne den zweiten Begriff im gleichen Thema|NICHT|„Betriebssystem“ NICHT DOS|Themen, die „Betriebssystem“ aber nicht „DOS“ enthalten.|  
|Beide Begriffe nah beieinander in einem Thema|NAH|Benutzer NAH Kernel|Themen mit „Benutzer“ in der Nähe von „Kernel“.|  
  
## <a name="see-also"></a>Siehe auch  
 [Tipps zur Volltextsuche](../ide/full-text-search-tips.md)   
 [Suchen nach Informationen](../ide/locate-information.md)




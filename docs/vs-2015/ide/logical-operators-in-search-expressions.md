---
title: Logische Operatoren in Suchausdrücken | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 66d6aa6a11ef0ce308c5ba2b089aaa8170b6441f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54760069"
---
# <a name="logical-operators-in-search-expressions"></a>Logische Operatoren in Suchausdrücken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von logischen Operatoren können Sie Ihre Suche nach Inhalten eingrenzen, indem Sie aus einfachen Suchausdrücken komplexere erstellen. Wie in der folgenden Tabelle dargestellt, kann mit logischen Operatoren angegeben werden, wie viele Suchausdrücke in einer Suchabfrage kombiniert werden sollen.  
  
> [!IMPORTANT]
>  Sie müssen logische Operatoren in Großbuchstaben eingeben, damit sie von der Suchmaschine erkannt werden.  
  
|Suchen nach|Verwendung|Beispiel|Ergebnis|  
|-------------------|---------|-------------|------------|  
|Beide Begriffe im gleichen Thema|UND|dib UND palette|Themen, die sowohl „Dib“ als auch „Palette“ enthalten.|  
|Einer der Begriffe in einem Thema|ODER|Raster ODER Vektor|Themen, die entweder „Raster“ oder „Vektor“ enthalten.|  
|Erster Begriff ohne den zweiten Begriff im gleichen Thema|NICHT|„Betriebssystem“ NICHT DOS|Themen, die „Betriebssystem“ aber nicht „DOS“ enthalten.|  
|Beide Begriffe nah beieinander in einem Thema|NAH|Benutzer NAH Kernel|Themen mit „Benutzer“ in der Nähe von „Kernel“.|  
  
## <a name="see-also"></a>Siehe auch  
 [Tipps zur Volltextsuche](../ide/full-text-search-tips.md)   
 [Suchen nach Informationen](../ide/locate-information.md)

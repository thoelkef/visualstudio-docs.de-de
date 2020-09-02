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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d56f2dfc2924008a6be293fe1498f0ffe32abaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651442"
---
# <a name="logical-operators-in-search-expressions"></a>Logische Operatoren in Suchausdrücken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von logischen Operatoren können Sie Ihre Suche nach Inhalten eingrenzen, indem Sie aus einfachen Suchausdrücken komplexere erstellen. Wie in der folgenden Tabelle dargestellt, kann mit logischen Operatoren angegeben werden, wie viele Suchausdrücke in einer Suchabfrage kombiniert werden sollen.

> [!IMPORTANT]
> Sie müssen logische Operatoren in Großbuchstaben eingeben, damit sie von der Suchmaschine erkannt werden.

|Suchen nach|Verwendung|Beispiel|Ergebnis|
|-------------------|---------|-------------|------------|
|Beide Begriffe im gleichen Thema|UND|dib UND palette|Themen, die sowohl „Dib“ als auch „Palette“ enthalten.|
|Einer der Begriffe in einem Thema|ODER|Raster ODER Vektor|Themen, die entweder „Raster“ oder „Vektor“ enthalten.|
|Erster Begriff ohne den zweiten Begriff im gleichen Thema|NICHT|„Betriebssystem“ NICHT DOS|Themen, die „Betriebssystem“ aber nicht „DOS“ enthalten.|
|Beide Begriffe nah beieinander in einem Thema|NEAR|Benutzer NAH Kernel|Themen mit „Benutzer“ in der Nähe von „Kernel“.|

## <a name="see-also"></a>Weitere Informationen
 [Tipps für die voll Text Suche](../ide/full-text-search-tips.md) [finden Sie Informationen](../ide/locate-information.md)

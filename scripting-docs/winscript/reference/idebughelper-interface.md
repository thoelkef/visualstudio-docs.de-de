---
title: IDebugHelper-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1708b742a484a2e7d6d48cf759f15c08711e13d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979187"
---
# <a name="idebughelper-interface"></a>IDebugHelper-Schnittstelle
Dient als Factory für Objektkataloge und einfacher Verbindungspunkt. Prozessbasierter Debug-Manager (PDM) implementiert diese Schnittstelle, die von der Skript-Engines verwendet wird.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugHelper` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Gibt einen Eigenschaftenbrowser, der umschließt eine Variante zurück.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Gibt einen Eigenschaftenbrowser, der eine Variante umschließt und ermöglicht die benutzerdefinierte Konvertierung von VARIANT-Werten oder VARTYPE-Typen in Zeichenfolgen zurück.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Gibt eine Ereignisschnittstelle, die dient als Wrapper für einen bestimmten `IDispatch` Objekt.|
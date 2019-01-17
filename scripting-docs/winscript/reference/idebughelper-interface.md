---
title: IDebugHelper-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ba760dc15cc0a3d3f2f0d80f3a16c5621582bc11
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347475"
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
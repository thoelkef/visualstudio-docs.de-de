---
title: IDebugFormatter-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 353a85ab51252c92086fa478d95b2e29ab3db62d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348034"
---
# <a name="idebugformatter-interface"></a>IDebugFormatter-Schnittstelle
Ermöglicht, dass eine Sprache oder IDE den Wechsel zwischen VARIANT-Werten oder VARTYPE-Typen und -Zeichenfolgen anpasst.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugFormatter` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Gibt eine Zeichenfolge, die den angegebenen VARIANT-Wert darstellt.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Gibt eine Variante, die die angegebene Zeichenfolge enthält.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Gibt eine Zeichenfolge, die den angegebenen VARTYPE-Wert darstellt.|
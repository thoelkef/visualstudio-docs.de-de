---
title: Iscriptentry-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575398"
---
# <a name="iscriptentry-interface"></a>IScriptEntry-Schnittstelle
Ein Objekt, das die `IScriptEntry`-Schnittstelle implementiert, stellt entweder einen Skriptblock oder ein Funktions Objekt dar.  
  
 Zusätzlich zu den Methoden, die von `IScriptNode` geerbt werden, macht die `IScriptEntry`-Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Gibt den Text zurück, der dem Text eines `IScriptEntry` Skript Blocks, eines Funktions Blocks oder eines Scriptlets entspricht.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Gibt den Elementnamen zurück, der ein `IScriptEntry` Objekt identifiziert.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Gibt für Einträge, die ein einzelnes Objekt (z. b. eine Funktion) darstellen, den Namen des Objekts zurück.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Gibt die Startposition und die Länge eines Eintrags zurück.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Gibt Typinformationen für ein `IScriptEntry` Funktions Objekt zurück.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Gibt den Text zurück, der einem `IScriptEntry` Skriptblock entspricht, oder den Quellcode, der in einem `IScriptScriptlet`-Ereignishandler enthalten ist.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Legt den Text fest, der im Hauptteil eines `IScriptEntry` Skript Blocks oder eines `IScriptScriptlet` Scriptlets liegt.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Legt den Elementnamen fest, der ein `IScriptEntry` Objekt identifiziert.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Für Einträge, die ein einzelnes Objekt darstellen (z. b. eine Funktion), wird der Name des Objekts festgelegt.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Legt Typinformationen für ein `IScriptEntry` Funktions Objekt fest.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Legt den Text fest, der einem `IScriptEntry` Skriptblock entspricht, oder den Quellcode, der in einem `IScriptScriptlet`-Ereignishandler enthalten ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)
---
title: IScriptEntry-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9d7b33e2e5c90d5c489fe283575b4a2e45671f9a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349347"
---
# <a name="iscriptentry-interface"></a>IScriptEntry-Schnittstelle
Ein Objekt, implementiert die `IScriptEntry` Schnittstelle darstellt, entweder ein Skriptblock oder ein Funktionsobjekt.  
  
 Zusätzlich zu den von geerbten Methoden `IScriptNode`, `IScriptEntry` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Gibt den Text zurück, der entspricht dem Textkörper der ein `IScriptEntry` Skriptblock, Funktionsblock oder Scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Gibt zurück, der Name des Elements, das identifiziert eine `IScriptEntry` Objekt.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Einträge, die ein einzelnes Objekt (z. B. eine Funktion) darstellen, gibt den Namen des Objekts zurück.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Gibt die Startposition und Länge eines Eintrags.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Gibt die Typinformationen für ein `IScriptEntry` Function-Objekt.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Gibt den Text zurück, das entspricht, einer `IScriptEntry` Skriptblock oder der Quellcode, der in enthalten ist ein `IScriptScriptlet` -Ereignishandler.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Legt den Text, der im Text einer `IScriptEntry` Skriptblock oder eine `IScriptScriptlet` Scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Legt den Namen, der identifiziert eine `IScriptEntry` Objekt.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Einträge, die ein einzelnes Objekt (z. B. eine Funktion) darstellen, legt den Namen des Objekts.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Legt die Typinformationen für ein `IScriptEntry` Function-Objekt.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Legt den Text, der entspricht einer `IScriptEntry` Skriptblock oder der Quellcode, der in enthalten ist ein `IScriptScriptlet` -Ereignishandler.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)
---
title: IScriptEntry-Schnittstelle | Microsoft Docs
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
ms.openlocfilehash: a785be8777cf3400f7723c24f1022bad6e22e330
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729810"
---
# <a name="iscriptentry-interface"></a>IScriptEntry-Schnittstelle
Ein Objekt, implementiert die `IScriptEntry` Schnittstelle darstellt, entweder ein Skriptblock oder ein Funktionsobjekt.  
  
 Zusätzlich zu den von geerbten Methoden `IScriptNode`, `IScriptEntry` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Den Text, entspricht dem Nachrichtentext gibt eine `IScriptEntry` Skriptblock Funktionsblocks oder Scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Gibt zurück, der Name des Elements identifiziert eine `IScriptEntry` Objekt.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Einträge, die ein einzelnes Objekt (z. B. eine Funktion) darstellen, gibt den Namen des Objekts zurück.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Gibt die Startposition und Länge eines Eintrags an.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Gibt Informationen zum Eingeben einer `IScriptEntry` Function-Objekt.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Gibt den Text, entspricht einer `IScriptEntry` Skriptblock oder der Quellcode, der in enthalten ist ein `IScriptScriptlet` -Ereignishandler.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Legt den Text, der im Text einer `IScriptEntry` Skriptblock oder eine `IScriptScriptlet` Scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Der Elementname, der identifiziert legt ein `IScriptEntry` Objekt.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Für Einträge, die ein einzelnes Objekt (z. B. eine Funktion) darstellen, wird der Name des Objekts.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Legt die Typinformationen für ein `IScriptEntry` Function-Objekt.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Legt den Text, der entspricht einer `IScriptEntry` Skriptblock oder der Quellcode, der in enthalten ist ein `IScriptScriptlet` -Ereignishandler.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)
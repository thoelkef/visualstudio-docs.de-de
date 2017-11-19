---
title: IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.CreateInstanceAtDebugger
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6495c2d8782d1128700bdfb6d4081b80ffae878
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Ermöglicht die Erstellung von Objekten im Debuggerprozess in Code vorgesehen, Out-of-Process an den Debugger.  
  
> [!IMPORTANT]
>  Diese Methode sollte nicht implementiert werden, da dadurch nicht vertrauenswürdigen Code auf beliebige Objekte in eine vertrauenswürdige Debuggerthread zu erstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rclsid`  
 [in] Klassenbezeichner (CLSID) des zu erstellenden Objekts.  
  
 `pUnkOuter`  
 [in] Wenn `NULL`, das Objekt wird nicht als Teil eines Aggregats erstellt. Andernfalls `pUnkOuter` ist ein Zeiger auf des aggregatobjekts `IUnknown` Schnittstelle (steuernde `IUnknown`).  
  
 `dwClsContext`  
 [in] Kontext für die Ausführung von ausführbarem Code. Die Werte stammen aus der Enumeration `CLSCTX`.  
  
 `riid`  
 [in] Der Schnittstellenbezeichner verwendet, um die Kommunikation mit dem Objekt.  
  
 `ppvObject`  
 [out] Adresse des Zeigervariable, die den Schnittstellenzeiger in angeforderte empfängt `riid`. Nach erfolgreicher Rückkehr *`ppvObject` enthält den angeforderten Schnittstellenzeiger auf. Bei einem Ausfall \* `ppvObject` enthält `NULL`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode delegiert an `CoCreateInstance`.  
  
 Die Methode wird derzeit nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)
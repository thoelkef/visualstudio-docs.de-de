---
title: IDebugProcessQueryProperties::QueryProperties | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37abff77fa0c969be7186413f0e3e2531c8d94d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915398"
---
# <a name="idebugprocessquerypropertiesqueryproperties"></a>IDebugProcessQueryProperties::QueryProperties
Diese Methodenabfragen für eine angegebene Eigenschaftenwerte des des Debugvorgangs zur Verfügung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT QueryProperties(  
   ULONG                  celt,  
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,  
   VARIANT               *rgtPropValues);  
```  
  
```csharp  
int QueryProperties(  
   uint                       celt,  
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,  
   out object[ ]              rgtPropValues);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Größe der Arrays, die die Definitionen von Eigenschaften und Eigenschaftswerte enthält.  
  
 `dwPropType`  
 [in] Ein Array, das Definitionen der abgefragten Eigenschaften enthält. Mögliche Werte sind:  
  
- PROCESS_PROPERTY_COMMAND_LINE = 1  
  
- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2  
  
- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3  
  
  `pvarPropValue`  
  [out] Ein Array mit den Eigenschaftswerten.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird nur selten verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
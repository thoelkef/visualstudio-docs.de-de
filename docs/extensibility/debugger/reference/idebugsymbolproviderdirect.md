---
title: IDebugSymbolProviderDirect | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcbee53b2f3d0a5a4fc45ab7e55bbb2a0cbe106a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931127"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Stellt einen symbolanbieter, die direkten Zugriff auf Metadaten und Core-Symbol-Schnittstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Ruft den Bezeichner der Anwendungsdomäne Wenn Sie die debugadresse ab.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Ruft Informationen über die Module in der Gruppe "Symbol" ab.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Ruft Informationen über die Symbol-Gruppe, die Mitglied der symbolanbieter ist.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Ruft die Informationen zum Importieren der Metadaten ab.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Ruft Informationen über die Methode an der angegebenen Debug-Adresse ab.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Ruft einen Symbolreader für nicht verwalteten Code ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle kann anstelle von den meisten anderen symbolanbieterschnittstellen verwendet werden. Es bietet direkten Zugriff auf die Metadaten und `CorSym` Schnittstellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
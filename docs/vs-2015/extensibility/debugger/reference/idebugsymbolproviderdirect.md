---
title: IDebugSymbolProviderDirect | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c0d8ea7a4d01b3fe18eccab67adfadb1a62cd75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514370"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugSymbolProviderDirect](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolproviderdirect).  
  
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

